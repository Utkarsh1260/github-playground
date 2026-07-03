# Conventional Git Commits

Git commit prefixes follow a standard called:

```txt
Conventional Commits
```

These prefixes describe the type/category of change made in a project.

Using proper commit messages helps keep GitHub repositories clean, organized, and professional.

---

# Common Git Commit Prefixes

| Prefix | Meaning |
|--------|---------|
| `feat:` | New feature added |
| `fix:` | Bug fixed |
| `docs:` | Documentation changes |
| `style:` | Formatting/UI/style changes |
| `refactor:` | Code improved without changing behavior |
| `test:` | Added or updated tests |
| `chore:` | Miscellaneous maintenance work |
| `perf:` | Performance improvements |

---

# Example Commit Messages

## Feature Commit

```bash
git commit -m "feat: add authentication system"
```

Used when adding a new feature or functionality.

---

## Bug Fix Commit

```bash
git commit -m "fix: correct login validation issue"
```

Used when fixing bugs or errors.

---

## Refactor Commit

```bash
git commit -m "refactor: simplify grading system logic"
```

Used when improving code structure without changing functionality.

---

## Documentation Commit

```bash
git commit -m "docs: update README with setup steps"
```

Used for:

- README updates
- Notes
- Documentation improvements
- Instructions

---

## Style Commit

```bash
git commit -m "style: improve button spacing"
```

Used for:

- UI styling
- Formatting changes
- Indentation
- CSS improvements

---

## Chore Commit

```bash
git commit -m "chore: organize project structure"
```

Used for:

- Project setup
- Folder organization
- Dependency updates
- General maintenance work

---

# Why Use Conventional Commits?

Using proper commit prefixes makes repositories more professional and easier to manage.

---

# Benefits

- Keeps commit history clean
- Makes project updates easier to understand
- Improves team collaboration
- Helps maintain large projects
- Supports automatic changelog generation
- Makes GitHub repositories look professional

---

# Professional Example Commit History

```txt
feat: add user authentication
fix: resolve navbar alignment issue
docs: update installation guide
refactor: optimize API request handling
style: improve landing page spacing
chore: update project folders
```

This creates a clean and industry-standard Git history.

---

# Final Recommendation

While working on GitHub projects:

- Write meaningful commit messages
- Use conventional commit prefixes
- Keep commit history organized
- Make commits small and understandable

Example:

```bash
git commit -m "feat: add portfolio landing page"
```