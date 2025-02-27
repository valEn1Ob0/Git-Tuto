# Git Tags and Releases

## 🏷️ Understanding Tags

Tags are references that point to specific points in Git history. They are typically used to mark version releases.

## 📌 Types of Tags

### Lightweight Tags
```bash
# Create lightweight tag
git tag v1.0.0

# List all tags
git tag

# Show tag info
git show v1.0.0
```

### Annotated Tags (Recommended)
```bash
# Create annotated tag
git tag -a v1.0.0 -m "Release version 1.0.0"

# List tags with annotations
git tag -n

# Show detailed tag info
git show v1.0.0
```

## 🚀 Working with Tags

### Creating Tags
```bash
# Tag current commit
git tag -a v1.0.0 -m "Release version 1.0.0"

# Tag specific commit
git tag -a v0.9.0 abc123f -m "Beta release"
```

### Sharing Tags
```bash
# Push specific tag
git push origin v1.0.0

# Push all tags
git push origin --tags
```

### Managing Tags
```bash
# Delete local tag
git tag -d v1.0.0

# Delete remote tag
git push origin --delete v1.0.0

# Checkout specific tag
git checkout v1.0.0
```

## 📦 GitHub/GitLab Releases

### Creating Releases
1. Go to repository on GitHub/GitLab
2. Navigate to "Releases" section
3. Click "Create new release"
4. Select or create a tag
5. Add release notes
6. Optionally attach binaries

### Release Notes Best Practices
- List new features
- Document breaking changes
- Include upgrade instructions
- Credit contributors
- Link to relevant issues/PRs

## 🔖 Version Numbering

### Semantic Versioning (MAJOR.MINOR.PATCH)
- MAJOR: Breaking changes
- MINOR: New features, backwards compatible
- PATCH: Bug fixes, backwards compatible

Example: v2.1.3

## 📝 Best Practices

1. Always use annotated tags for releases
2. Follow semantic versioning
3. Write detailed release notes
4. Tag only stable commits
5. Keep tags synchronized with releases

## 🔄 Common Workflows

### Release Process
```bash
# Ensure you're on main branch
git switch main

# Pull latest changes
git pull origin main

# Create annotated tag
git tag -a v1.0.0 -m "Release version 1.0.0"

# Push tag
git push origin v1.0.0

# Create release on GitHub/GitLab
# Add release notes and binaries
```

### Hotfix Process
```bash
# Create hotfix branch from tag
git checkout -b hotfix-1.0.1 v1.0.0

# Make fixes and commit
git commit -m "Fix critical bug"

# Create new tag
git tag -a v1.0.1 -m "Hotfix release v1.0.1"

# Push changes and tag
git push origin hotfix-1.0.1
git push origin v1.0.1
``` 