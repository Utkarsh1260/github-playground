# Git and Linux Commands – Notes

## 📚 Table of Contents

| S.No. | Topic                       | Short Description                                                                  |
| ----- | --------------------------- | ---------------------------------------------------------------------------------- |
| 1     | File and Directory Commands | Create, read, append, list, and delete files and directories using Linux commands. |
| 2     | Git History and Changes     | View commit history and compare file changes using Git commands.                   |
| 3     | Tracking Empty Directories  | Use `.gitkeep` to track directories containing no other files.                     |
| 4     | Git Workflow and Stages     | Understand the Working Directory, Staging Area, and Repository.                    |
| 5     | Git Restore and Unstaging   | Unstage files and discard unstaged changes.                                        |
| 6     | Git Reset                   | Understand soft, mixed, and hard resets to undo commits and manage changes.        |
| 7     | Git Safety Practices        | Understand data-loss risks and precautions when using destructive commands.        |

---

## 1. File and Directory Commands

| Command                     | Explanation                                                                                                                    | Example / Output                                                                                    |
| --------------------------- | ------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------- |
| `echo "hello" > file.txt`   | Creates `file.txt` and writes `hello` into it. If the file already exists, its previous content is overwritten.                | `hello`                                                                                             |
| `cat file.txt`              | Displays the contents of a file in the terminal.                                                                               | Displays `hello`                                                                                    |
| `echo "hello1" >> file.txt` | Appends new content to the file without removing its existing content.                                                         | Adds `hello1` on a new line only if you include `\n` or use a separate command that adds a newline. |
| `ls -a`                     | Lists all files and directories, including hidden ones.                                                                        | Displays files such as `.git` and `.gitignore`.                                                     |
| `rm -rf *`                  | Deletes non-hidden files and directories in the current directory, including nested contents, without asking for confirmation. | Dangerous: Deleted data may be difficult or impossible to recover.                                  |

### Understanding command components

| Component | Meaning                                                              |
| --------- | -------------------------------------------------------------------- |
| `echo`    | Prints text to the terminal or sends it to a file using redirection. |
| `>`       | Redirects output to a file, replacing its existing content.          |
| `>>`      | Redirects output to a file by appending to its existing content.     |
| `cat`     | Displays or combines file contents.                                  |
| `ls`      | Lists directory contents.                                            |
| `-a`      | Shows all entries, including hidden entries.                         |
| `rm`      | Removes files or directories.                                        |
| `-r`      | Removes directories recursively, including their contents.           |
| `-f`      | Forces removal without prompting for confirmation in normal cases.   |
| `*`       | A wildcard matching non-hidden names in the current directory.       |

Important: `rm -rf *` does not normally delete hidden entries such as `.git`. Be extremely careful when running destructive commands.

## 2. Git Commands

| Command                         | Purpose                     | Explanation                                                                                   |
| ------------------------------- | --------------------------- | --------------------------------------------------------------------------------------------- |
| `git log`                       | View commit history         | Displays commit details, including commit IDs, authors, dates, and messages.                  |
| `git log --oneline`             | View compact commit history | Displays each commit in a single line.                                                        |
| `git diff`                      | View unstaged changes       | Shows the exact line-by-line differences between your working directory and the staging area. |
| `git restore filename`          | Discard unstaged changes    | Restores a file to its staged version, or its last committed version if it is not staged.     |
| `git restore --staged filename` | Unstage a file              | Removes the file from the staging area without discarding its working-directory changes.      |

### What is `.gitkeep`?

Git does not track empty directories by default. A common convention is to create a file named `.gitkeep` inside an otherwise empty directory so that Git can track the directory through that file.

Example folder structure:

```
project/
├── src/
│   └── .gitkeep
└── README.md
```

`.gitkeep` is not a special Git command or feature. It is simply a conventionally named placeholder file.

## 3. The Three Main Areas in Git

Git manages your changes through three main areas.

1\. Working Directory (WD)

Where you create or modify files.

`git add filename`

2\. Staging Area (SA)

Changes selected for the next commit.

`git commit -m "message"`

3\. Local Repository (Repo)

Stores committed snapshots and project history.

## 4. Git Reset Commands

`git reset` moves the current branch reference to an earlier commit. Depending on the option used, it also changes the staging area and working directory.

### A. Soft Reset

Command:

```
git reset --soft HEAD~1
```

- Moves the current branch back by one commit.
- Keeps the changes from that commit in the staging area.
- Does not discard the changes.

You can replace `1` with another number, such as `HEAD~2`, to move back two commits.

Movement

Before reset: changes are committed.

Repository

Staging Area

The changes from the removed commit remain staged.

To unstage the changes afterward:

```
git restore --staged filename
```

This moves the changes from the staging area back to the working directory without deleting them.

### B. Mixed Reset (Default)

Command:

```
git reset HEAD~1
```

This is equivalent to:

```
git reset --mixed HEAD~1
```

- Moves the current branch back by one commit.
- Resets the staging area.
- Keeps the changes in the working directory as unstaged changes.

Movement

Repository

Working Directory

The changes remain available but are no longer staged.

You can stage the changes again with `git add filename` or discard an unstaged file's changes using:

```
git restore filename
```

Warning: The latter discards the file's unstaged changes. If you have both staged and unstaged changes, it does not remove the staged version of those changes.

### C. Hard Reset

Command:

```
git reset --hard HEAD~1
```

- Moves the current branch back by one commit.
- Resets the staging area.
- Resets tracked files in the working directory to match the target commit.

Movement

Repository

Discard changes

Danger: Uncommitted changes to tracked files can be permanently lost.

Hard reset does not normally delete untracked files and directories. However, changes discarded by a hard reset may be difficult to recover. Use it only when you understand which changes will be lost.

## 5. Quick Comparison: Git Reset

| Feature                             | `--soft` | `--mixed` (default) | `--hard`                    |
| ----------------------------------- | -------- | ------------------- | --------------------------- |
| Moves branch to an earlier commit   | Yes      | Yes                 | Yes                         |
| Resets staging area                 | No       | Yes                 | Yes                         |
| Resets tracked working files        | No       | No                  | Yes                         |
| Changes remain staged               | Yes      | No                  | No                          |
| Changes remain in working directory | Yes      | Yes                 | No, tracked files are reset |
| Risk of losing uncommitted changes  | Low      | Low                 | High                        |

