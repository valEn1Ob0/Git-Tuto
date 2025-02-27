# Git Basics

## 📋 Table of Contents
1. [Core Concepts](#core-concepts)
2. [Essential Commands](#essential-commands)
3. [Working with Remote Repositories](#working-with-remote-repositories)
4. [Basic Workflow Example](#basic-workflow-example)
5. [Modern Git Commands](#modern-git-commands)
6. [Handling Merge Conflicts](#handling-merge-conflicts)
7. [Common Issues and Solutions](#common-issues-and-solutions)
8. [Next Steps](#next-steps)

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
# Configure line endings (Windows)
git config --global core.autocrlf true
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

## 🔄 Modern Git Commands

### Switch and Restore (Git 2.23+)
```bash
# Switch branches (replaces git checkout)
git switch main
git switch -c new-feature  # Create and switch

# Restore files (replaces git checkout -- <file>)
git restore <file>  # Discard working directory changes
git restore --staged <file>  # Unstage files
git restore --source=HEAD~1 <file>  # Restore from specific commit
```

## 🔀 Handling Merge Conflicts

### Understanding Conflicts
When Git can't automatically merge changes, you'll see:
- `<<<<<<<` HEAD (current changes)
- `=======` divider
- `>>>>>>>` branch-name (incoming changes)

### Resolving Conflicts
```bash
# 1. Identify conflicted files
git status

# 2. Open and edit conflicted files
# Remove conflict markers and keep desired changes

# 3. Mark as resolved
git add <resolved-file>

# 4. Complete the merge
git commit -m "Resolve merge conflicts"
```

### Preventing Conflicts
```bash
# Update your branch before making changes
git pull origin main

# Check potential conflicts before merging
git fetch origin
git diff main origin/main
```

### Aborting a Merge
```bash
# If you want to start over
git merge --abort
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
- Practice [resolving merge conflicts](git-conflicts.md)
