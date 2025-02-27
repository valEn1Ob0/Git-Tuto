# Advanced Git

## 🔄 Advanced Branch Management

### Branch Strategies
```bash
# Create and switch to feature branch
git switch -c feature/user-authentication

# Rebase feature branch onto main
git switch feature/user-authentication
git rebase main

# Interactive rebase for cleaning history
git rebase -i HEAD~3
```

## 🎯 Advanced Operations

### Stashing Changes
```bash
# Save working directory changes
git stash save "WIP: implementing login form"

# List stashes
git stash list

# Apply and remove stash
git stash pop

# Apply without removing
git stash apply stash@{0}
```

### Cherry-picking
```bash
# Apply specific commit to current branch
git cherry-pick abc123f

# Cherry-pick without committing
git cherry-pick -n abc123f
```

### Reflog - Recovery Tool
```bash
# View reflog history
git reflog

# Recover deleted branch
git checkout -b recovered-branch HEAD@{2}
```

## 🔍 Advanced History Management

### History Rewriting
```bash
# Modify last commit
git commit --amend --no-edit

# Squash last 3 commits
git reset --soft HEAD~3
git commit -m "Combined feature implementation"
```

### Bisect - Bug Hunting
```bash
# Start bisect
git bisect start
git bisect bad  # Current version is bad
git bisect good v1.0.0  # Last known good version

# Git will checkout commits automatically
# Mark each version
git bisect good  # or
git bisect bad

# End bisect
git bisect reset
```

## 🤝 Advanced Team Workflows

### Submodules
```bash
# Add submodule
git submodule add https://github.com/user/repo

# Update submodules
git submodule update --init --recursive
```

### Git Hooks
```bash
# Location: .git/hooks/pre-commit
#!/bin/sh
npm test  # Run tests before commit
```

## 🔒 Security and Large Files

### Git LFS (Large File Storage)
```bash
# Install Git LFS
git lfs install

# Track large files
git lfs track "*.psd"
git add .gitattributes
```

### GPG Signing Commits
```bash
# Configure GPG key
git config --global user.signingkey <your-key-id>

# Sign commits
git commit -S -m "Signed commit message"
```

## 🚀 Real-World Example: Feature Implementation

```bash
# Start new feature
git switch -c feature/payment-gateway

# Make changes and commit
git add .
git commit -m "Add payment gateway integration"

# Update with main branch changes
git fetch origin
git rebase origin/main

# Squash commits before merge
git rebase -i HEAD~3

# Push to remote
git push origin feature/payment-gateway --force-with-lease
```

## 📚 Best Practices
- Always use `--force-with-lease` instead of `--force`
- Keep commits atomic and focused
- Write meaningful commit messages
- Use branch naming conventions
- Regularly sync with the main branch
- Use Git hooks for quality control

## 🔗 Further Reading
- [Git Internals](https://git-scm.com/book/en/v2/Git-Internals-Plumbing-and-Porcelain)
- [Advanced Git Workflows](team-workflows.md)