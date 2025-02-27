# Git Security Best Practices

## 🔒 Authentication and Access

### SSH Keys
```bash
# Generate new SSH key
ssh-keygen -t ed25519 -C "your.email@example.com"

# Add key to ssh-agent
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519

# Copy public key (add to GitHub/GitLab)
cat ~/.ssh/id_ed25519.pub
```

### Two-Factor Authentication
1. Enable 2FA in your Git hosting service
2. Configure authentication app
3. Save backup codes securely
4. Update Git credentials locally

## 🛡️ Repository Security

### Sensitive Data Protection
```bash
# Remove sensitive file and its history
git filter-branch --force --index-filter \
  "git rm --cached --ignore-unmatch PATH_TO_FILE" \
  --prune-empty --tag-name-filter cat -- --all

# Use .gitignore for sensitive files
echo "secrets.json" >> .gitignore
echo "*.key" >> .gitignore
```

### Signing Commits
```bash
# Configure GPG key
git config --global user.signingkey YOUR_GPG_KEY_ID
git config --global commit.gpgsign true

# Sign commits
git commit -S -m "Signed commit message"

# Verify signatures
git verify-commit HEAD
```

## 🔐 Secret Management

### Using Environment Variables
```bash
# Store credentials in environment
export API_KEY="your-api-key"

# Use in scripts
api_key = os.getenv('API_KEY')
```

### Git-Secret Tool
```bash
# Initialize git-secret
git secret init

# Add user's public key
git secret tell user@email.com

# Hide sensitive file
git secret hide

# Reveal when needed
git secret reveal
```

## 🚫 Access Control

### Branch Protection Rules
1. Require pull request reviews
2. Enforce signed commits
3. Require status checks
4. Restrict force pushes

### Repository Settings
1. Enable vulnerability alerts
2. Configure dependency updates
3. Set up code scanning
4. Enable secret scanning

## 📝 Security Policies

### Security Policy File
```markdown
# SECURITY.md
## Reporting Security Issues
## Supported Versions
## Security Update Process
## Security Best Practices
```

### Code of Conduct
```markdown
# CODE_OF_CONDUCT.md
## Our Standards
## Enforcement
## Scope
## Contact Information
```

## 🔍 Security Auditing

### Repository Audit
```bash
# Check git history for secrets
git log -p | grep -i "password\|secret\|key"

# Review large files
git rev-list --objects --all |
  git cat-file --batch-check='%(objecttype) %(objectname) %(objectsize) %(rest)' |
  sed -n 's/^blob //p' |
  sort -rn -k2 |
  head -10
```

### Dependencies Audit
```bash
# NPM audit
npm audit

# Python dependencies
pip list --outdated
```

## ⚡ Quick Security Checklist

1. [ ] Use SSH keys for authentication
2. [ ] Enable 2FA
3. [ ] Sign commits with GPG
4. [ ] Configure branch protection
5. [ ] Review .gitignore
6. [ ] Audit for secrets
7. [ ] Keep dependencies updated
8. [ ] Use environment variables
9. [ ] Implement security policy
10. [ ] Regular security audits

## 🚀 Implementation Guide

1. Repository Setup
   ```bash
   # Initialize secure repository
   git init
   git config --global user.signingkey YOUR_GPG_KEY
   git config --global commit.gpgsign true
   ```

2. Daily Workflow
   ```bash
   # Before committing
   git secrets --scan
   git diff --staged

   # Secure commit
   git commit -S -m "Secure commit message"
   ```

3. Regular Maintenance
   ```bash
   # Update dependencies
   npm audit fix
   
   # Check for exposed secrets
   git-secrets --scan-history
   ``` 