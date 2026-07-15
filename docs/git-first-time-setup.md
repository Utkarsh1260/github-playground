# Git Global Configuration

Run the following commands on your PC to configure Git and fix common commit issues.

## 1. Set Your Git Username

```bash
git config --global user.name "Utkarsh1260"
```

> Replace `"Utkarsh1260"` with your GitHub username if needed.

---

## 2. Set Your Git Email

```bash
git config --global user.email "your-gmail-used-to-create-github-account@gmail.com"
```

> Use the same email address that is associated with your GitHub account.

---

## 3. Set VS Code as the Default Git Editor

```bash
git config --global core.editor "code --wait"
```

> This makes Visual Studio Code the default editor for Git operations such as commit messages.

---

## 4. Configure Line Endings (Recommended for Windows & macOS)

```bash
git config --global core.autocrlf input
```

> This setting keeps line endings consistent across Windows, macOS, and Linux by converting CRLF to LF when committing.

---

## Verify Your Configuration

```bash
git config --global --list
```

This will display all your global Git configuration settings.
