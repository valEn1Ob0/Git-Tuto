# Git Interactive Exercises and Troubleshooting

[Previous content remains the same...]

## 🎯 Additional Advanced Exercises

### Exercise 4: Git Reflog Recovery
```bash
# Setup: Create and lose some work
git switch -c feature
echo "Important work" > important.txt
git add important.txt
git commit -m "Important changes"
git switch main
git branch -D feature  # Accidentally delete branch

# Task: Recover the deleted branch
# Solution:
git reflog  # Find the commit hash
git switch -c feature-recovered <hash>

# Verify:
cat important.txt
```

### Exercise 5: Interactive Rebase
```bash
# Setup: Create multiple commits
for i in {1..5}; do
    echo "Change $i" >> file.txt
    git add file.txt
    git commit -m "Change $i"
done

# Task: Reorganize commits
git rebase -i HEAD~5

# Operations to try:
# - Squash related commits
# - Reword commit messages
# - Drop unnecessary commits
# - Reorder commits
```

### Exercise 6: Submodule Management
```bash
# Task: Add and update submodules
git submodule add https://github.com/example/lib external/lib
git submodule update --init --recursive

# Make changes in submodule
cd external/lib
git switch -c custom-feature
echo "Custom change" > custom.txt
git add custom.txt
git commit -m "Add custom feature"

# Update main project
cd ../..
git add external/lib
git commit -m "Update submodule"
```

## 🔄 New Real-World Scenarios

### Scenario 4: Git Bisect with Tests
```bash
# Setup: Create test script
cat > test.sh << 'EOF'
#!/bin/bash
grep -q "bug" file.txt && exit 1 || exit 0
EOF
chmod +x test.sh

# Use bisect with automated test
git bisect start
git bisect bad HEAD
git bisect good v1.0
git bisect run ./test.sh

# Analyze results
git bisect log
git bisect reset
```

### Scenario 5: Large File Management
```bash
# Setup: Track large files with Git LFS
git lfs install
git lfs track "*.psd"
git lfs track "*.zip"
git add .gitattributes

# Add and commit large files
git add large-file.psd
git commit -m "Add design assets"

# Verify LFS tracking
git lfs ls-files
```

### Scenario 6: Multiple Remote Management
```bash
# Setup multiple remotes
git remote add upstream https://github.com/original/repo.git
git remote add staging https://github.com/staging/repo.git

# Sync with multiple remotes
git fetch --all
git switch main
git merge upstream/main
git push origin main
git push staging main
```

## 🛠️ Advanced Git Hooks Exercises

### Exercise 7: Custom Git Hooks
```bash
# Create pre-commit hook
cat > .git/hooks/pre-commit << 'EOF'
#!/bin/bash
files=$(git diff --cached --name-only --diff-filter=ACM | grep '\.js$')
if [ -n "$files" ]; then
    npm run lint $files
    if [ $? -ne 0 ]; then
        echo "Linting failed! Fix errors before committing."
        exit 1
    fi
fi
EOF
chmod +x .git/hooks/pre-commit

# Test the hook
echo "console.log('test')" > test.js
git add test.js
git commit -m "Test hook"
```

### Exercise 8: Git Attributes
```bash
# Setup custom diff strategy
cat > .gitattributes << 'EOF'
*.json diff=json
*.md diff=markdown
EOF

# Create custom diff driver
git config diff.json.textconv "python -m json.tool"

# Test with JSON file
echo '{"key": "value"}' > config.json
git add config.json
git diff --cached
```

## 🎮 Team Collaboration Scenarios

### Scenario 7: Code Review Workflow
```bash
# Setup feature branch
git switch -c feature/new-api
echo "API code" > api.js
git add api.js
git commit -m "Initial API implementation"

# Simulate review feedback
git switch -c review-feedback
echo "Review changes" >> api.js
git add api.js
git commit -m "Address review comments"

# Incorporate feedback
git switch feature/new-api
git merge review-feedback
git push origin feature/new-api
```

### Scenario 8: Release Management
```bash
# Create release branch
git switch -c release/2.0 main
echo "2.0.0" > VERSION
git add VERSION
git commit -m "Bump version to 2.0.0"

# Create release candidate
git tag -a v2.0.0-rc1 -m "Release candidate 1"
git push origin v2.0.0-rc1

# Simulate hotfix
git switch -c hotfix/security main
echo "Security fix" > security.patch
git add security.patch
git commit -m "Critical security fix"

# Cherry-pick to release
git switch release/2.0
git cherry-pick hotfix/security
git tag -a v2.0.1 -m "Security patch release"
```

## ✨ Git Workflow Integration Exercises

### Exercise 9: CI/CD Integration
```bash
# Setup GitHub Actions workflow
mkdir -p .github/workflows
cat > .github/workflows/ci.yml << 'EOF'
name: CI
on: [push, pull_request]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - run: npm test
EOF

git add .github/workflows/ci.yml
git commit -m "Add CI workflow"
```

### Exercise 10: Git Flow Implementation
```bash
# Initialize Git Flow
git flow init

# Feature development
git flow feature start new-feature
echo "Feature code" > feature.js
git add feature.js
git commit -m "Implement new feature"
git flow feature finish new-feature

# Release process
git flow release start 1.0.0
echo "1.0.0" > VERSION
git add VERSION
git commit -m "Bump version"
git flow release finish 1.0.0
``` 