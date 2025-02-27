# Git Quick Start Guide

## Prerequisites
- Git installed on your system
- Basic command line knowledge
- Text editor (VS Code recommended)

## 🔧 Initial Setup

### 1. Configure Git
```bash
# Set your identity
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# Set default editor (VS Code)
git config --global core.editor "code --wait"

# Configure line endings
# For Unix/Linux:
git config --global core.autocrlf input
# For Windows:
git config --global core.autocrlf true
```

### 2. Start a Project

#### Create a New Repository
```bash
# Initialize a new repository
git init my-project
cd my-project

# Create initial files
echo "# My Project" > README.md
```

#### Clone an Existing Repository
```bash
git clone https://github.com/username/repository.git
```

### 3. Basic Workflow

```bash
# Check status
git status

# Add files
git add README.md    # Single file
git add .            # All files

# Commit changes
git commit -m "Initial commit"

# Push to remote (if using GitHub)
git push origin main
```

## 📚 Next Steps
- Continue with [Git Basics](git-basics.md)
- Learn about [.gitignore](gitignore-guide.md)
- Explore [Team Workflows](team-workflows.md)

## 🆘 Common Issues
- [Permission denied (publickey)](https://docs.github.com/en/authentication/troubleshooting-ssh)
- [Git not recognized as a command](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)