# Team Workflows in Git

## 📊 Common Workflow Models

### 1. Git Flow
A robust workflow for larger projects:

```bash
# Create feature branch
git switch -c feature/new-feature develop

# After feature completion
git switch develop
git merge feature/new-feature
git branch -d feature/new-feature

# Create release
git switch -c release/1.0.0 develop
```

### 2. GitHub Flow
Simpler workflow focused on continuous delivery:

```bash
# Create feature branch
git switch -c feature-name main

# Push changes regularly
git push -u origin feature-name

# Create Pull Request via GitHub
# After review and approval, merge via GitHub UI
```

## 🤝 Collaboration Best Practices

### Pull Requests
```bash
# Create PR-ready branch
git switch -c feature/user-auth
git push -u origin feature/user-auth

# Update PR with main changes
git switch feature/user-auth
git fetch origin
git rebase origin/main
git push --force-with-lease
```

### Code Review Guidelines
- Keep changes small and focused
- Use meaningful commit messages
- Address all review comments
- Update branch with main regularly

## 🔄 Branch Management

### Protected Branches
```bash
# Main branch protection rules
- Require pull request reviews
- Require status checks
- No direct pushes
```

### Branch Naming Convention
```
feature/    # New features
bugfix/     # Bug fixes
hotfix/     # Urgent fixes
release/    # Release branches
docs/       # Documentation updates
```

## 👥 Team Collaboration Examples

### Feature Development
```bash
# Start new feature
git switch -c feature/payment-system
git push -u origin feature/payment-system

# Collaborate with team member
git fetch origin
git rebase origin/feature/payment-system

# Create PR when ready
git push origin feature/payment-system
```

### Conflict Resolution
```bash
# Handle merge conflicts
git fetch origin
git rebase origin/main

# Resolve conflicts in VS Code
git add .
git rebase --continue
git push --force-with-lease
```

## 🔒 Security and Access Control

### SSH Keys
```bash
# Generate SSH key
ssh-keygen -t ed25519 -C "your@email.com"

# Add to GitHub account
cat ~/.ssh/id_ed25519.pub
# Copy output to GitHub SSH keys
```

### GPG Signing
```bash
# Configure GPG signing
git config --global commit.gpgsign true
git config --global user.signingkey YOUR_KEY_ID
```

## 📈 Project Management Integration

### Issue Tracking
```bash
# Branch for specific issue
git switch -c feature/issue-123

# Commit message with issue reference
git commit -m "Implement login form #123"
```

## 🚀 CI/CD Integration

### GitHub Actions Example
```yaml
name: CI
on: [push, pull_request]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - run: npm test
```

## 📝 Documentation Standards

### Commit Messages
```
type(scope): description

- feat: New feature
- fix: Bug fix
- docs: Documentation
- style: Formatting
- refactor: Code restructuring
```

## 🔍 Monitoring and Maintenance

### Repository Health
```bash
# Check repo status
git remote show origin
git remote prune origin
git gc --aggressive
```