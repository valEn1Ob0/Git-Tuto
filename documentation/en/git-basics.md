# Git Basics

## 🌟 Core Concepts

### What is Git?
Git is a distributed version control system that tracks changes in your code over time.

### The Three States of Git
1. **Working Directory**: Where you modify files
2. **Staging Area**: Where you prepare changes for commit
3. **Git Repository**: Where Git stores the commit history

## 📝 Essential Commands

### Setting Up Git
```bash
# Configure your identity
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# Configure line endings (Unix)
git config --global core.autocrlf input
```

### Basic Operations
```bash
# Initialize a repository
git init

# Check status
git status
git status -s  # Short format

# Add files to staging
git add <file>     # Single file
git add .          # All files

# Commit changes
git commit -m "Descriptive message"
git commit -a -m "Add and commit in one step"

# View history
git log
git log --oneline  # Compact view
```

### Working with Remote Repositories
```bash
# Clone a repository
git clone <url>

# Add remote repository
git remote add origin <url>

# Push changes
git push origin main

# Get updates
git pull origin main
```

## 🔄 Basic Workflow Example

```bash
# Create a new feature
git checkout -b feature-name

# Make changes and track them
git add .
git commit -m "Add new feature"

# Push to remote
git push origin feature-name
```

## ⚠️ Common Issues and Solutions

### 1. Undoing Changes
```bash
# Discard changes in working directory
git restore <file>

# Unstage files
git restore --staged <file>

# Modify last commit
git commit --amend
```

### 2. File Operations
```bash
# Rename files
git mv old-name new-name

# Remove files
git rm file-name
```

## 📚 Next Steps
- Learn about [branching strategies](team-workflows.md)
- Explore [advanced Git features](git-advanced.md)
- Master [.gitignore patterns](gitignore-guide.md)