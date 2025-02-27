# Git History Investigation Guide

## 🔍 Basic History Commands

### Git Blame
```bash
# Basic blame
git blame filename.txt

# Ignore whitespace changes
git blame -w filename.txt

# Show specific line range
git blame -L 10,20 filename.txt

# Show commit details
git blame -l filename.txt

# Detect moved or copied lines
git blame -M filename.txt
```

### Git Log
```bash
# View file history
git log --follow filename.txt

# Show patches
git log -p filename.txt

# Show statistics
git log --stat filename.txt

# Show graph
git log --graph --oneline --all
```

## 🕵️ Advanced Investigation Techniques

### Finding Changes
```bash
# Search commit messages
git log --grep="bug fix"

# Search code changes
git log -S"function_name"

# Search regex patterns
git log -G"pattern.*"

# Find author's commits
git log --author="John"
```

### Investigating Lines
```bash
# Show line evolution
git blame -w -C -C -C filename.txt

# Find original commit for lines
git blame -w --reverse START..END filename.txt

# Track line moves between files
git log --follow -p filename.txt
```

## 📊 Code Archaeology

### Finding Bug Introduction
```bash
# Use bisect to find issues
git bisect start
git bisect bad HEAD
git bisect good v1.0
git bisect run test.sh
```

### Investigating Changes
```bash
# Show commit details
git show commit_hash

# Compare file versions
git diff commit1..commit2 filename.txt

# Find renamed files
git log --follow --name-status filename.txt
```

## 🔎 Advanced History Analysis

### Commit Range Analysis
```bash
# View commit range
git log commit1..commit2

# Compare branches
git log main..feature

# Show merge history
git log --merges
```

### File History
```bash
# Show file creation
git log --diff-filter=A -- filename.txt

# Show file deletion
git log --diff-filter=D -- filename.txt

# Show file modifications
git log --diff-filter=M -- filename.txt
```

## 🛠️ Investigation Tools

### Git Pickaxe
```bash
# Find string introduction
git log -S"string" --patch

# Find regex pattern changes
git log -G"pattern" --patch

# Search in specific files
git log -S"string" -- "*.js"
```

### Blame Ignore Revs
```bash
# Create .git-blame-ignore-revs
echo "commit_hash" > .git-blame-ignore-revs

# Use ignore file
git blame --ignore-revs-file .git-blame-ignore-revs
```

## 📈 Statistical Analysis

### Contribution Statistics
```bash
# Author statistics
git shortlog -sn

# Commit count by author
git log --author="name" --oneline | wc -l

# File change statistics
git log --stat --author="name"
```

### Code Evolution
```bash
# Track file size changes
git log --stat --oneline filename.txt

# Show file lifecycle
git log --follow --stat filename.txt
```

## 🔧 Practical Investigation Scenarios

### Scenario 1: Bug Investigation
```bash
# 1. Find relevant changes
git log -S"bug_related_string"

# 2. Check specific commit
git show commit_hash

# 3. Analyze file history
git blame -w -C filename.txt
```

### Scenario 2: Feature History
```bash
# 1. Find feature introduction
git log --grep="feature name"

# 2. Track file changes
git log --follow -p feature_file.txt

# 3. Review related commits
git show commit_hash
```

## 📝 Best Practices

1. Use specific search terms
2. Combine multiple commands
3. Verify findings
4. Document investigation process
5. Use appropriate flags

## 🚀 Advanced Tips

### Performance Optimization
```bash
# Use shallow clone
git clone --depth 1 repository_url

# Use partial clone
git clone --filter=blob:none repository_url

# Use sparse checkout
git sparse-checkout set directory/
```

### Complex Queries
```bash
# Multiple conditions
git log --grep="feature" --author="John" --since="1 week ago"

# Custom formats
git log --pretty=format:"%h - %an, %ar : %s"
```

## 🎯 Quick Reference

### Common Investigation Commands
```bash
git blame              # Line-by-line history
git log               # Commit history
git show              # Commit details
git diff              # Compare changes
git bisect            # Binary search
git shortlog          # Author summary
git log --follow      # File history
git log -S            # Content search
git log -G            # Pattern search
```

## 🔬 Advanced Investigation Techniques

### Git Notes Analysis
```bash
# Add note to commit
git notes add -m "Investigation note: Possible bug source" commit_hash

# Show notes with commits
git log --show-notes

# Search through notes
git log --notes-all | grep "bug"

# Push notes to remote
git push origin refs/notes/*
```

### Binary Search with Custom Script
```bash
# Create test script
cat > test.sh << 'EOF'
#!/bin/bash
# Custom test logic
if grep -q "ERROR" log.txt; then
    exit 1  # Bad commit
else
    exit 0  # Good commit
fi
EOF
chmod +x test.sh

# Run automated bisect
git bisect start HEAD v1.0
git bisect run ./test.sh
```

### Time-Based Investigation
```bash
# Find changes within time range
git log --since="2 weeks ago" --until="1 week ago"

# Find commits at specific times
git log --before="2023-01-01" --after="2022-12-31"

# Show timestamp details
git log --date=iso-strict
```

## 📊 Advanced Metrics Analysis

### Code Churn Analysis
```bash
# Track file changes over time
git log --numstat --pretty="%H" | awk '
NF==3 {plus+=$1; minus+=$2} 
END {print "Added: "plus"\nRemoved: "minus"\nChurn: "plus+minus}'

# Find most changed files
git log --pretty=format: --name-only | sort | uniq -c | sort -rg | head -10
```

### Author Contribution Analysis
```bash
# Analyze author patterns
git shortlog -sn --no-merges

# Show author activity times
git log --format='%ad' --date=iso | cut -d ' ' -f 2 | sort | uniq -c

# Find pair programming instances
git log --pretty=format:"%an, %cn" | sort | uniq -c | sort -nr
```

### Impact Analysis
```bash
# Find high-impact changes
git log --pretty=format: --name-only | sort | uniq -c | sort -rg

# Identify risky commits
git log --pretty=format:"%h - %an, %ar : %s" --diff-filter=M --stat
```

## 🔍 Deep Inspection Tools

### Commit Content Analysis
```bash
# Find specific code patterns
git log -p | grep -A 5 -B 5 "TODO"

# Track function changes
git log -L :function_name:file.js

# Find code duplication
git log -S"duplicate_pattern" --pickaxe-all
```

### Branch Analysis
```bash
# Find unmerged branches
git branch --no-merged main

# Show branch hierarchy
git show-branch --all

# Find orphaned commits
git fsck --lost-found
```

### Merge Analysis
```bash
# Show merge history
git log --merges --first-parent main

# Find conflicting files pattern
git log --cc -m --diff-filter=C

# Analyze merge frequency
git log --merges --format=format:"%cd" --date=short | uniq -c
```

## 🛠️ Custom Investigation Tools

### Custom Log Formats
```bash
# Create custom log format
git config --global alias.investigation \
    "log --pretty=format:'%C(yellow)%h%Creset %C(blue)%ad%Creset %s %C(red)%d%Creset %C(green)%an%Creset' --date=short"

# Use custom format
git investigation
```

### Investigation Scripts
```bash
# Create investigation helper
cat > git-investigate << 'EOF'
#!/bin/bash
# Search in commits and show context
git log -p -S"$1" --pickaxe-all
# Show related branches
git branch --contains $(git log -S"$1" --pretty=format:"%H" | head -1)
EOF
chmod +x git-investigate
```

### Custom Diff Tools
```bash
# Configure custom diff tool
git config --global diff.tool custom
git config --global difftool.custom.cmd 'diff-highlight "$LOCAL" "$REMOTE"'

# Use with investigation
git difftool commit1..commit2
```

## 📈 Performance Analysis

### Repository Size Analysis
```bash
# Find large files
git rev-list --objects --all |
  git cat-file --batch-check='%(objecttype) %(objectname) %(objectsize) %(rest)' |
  sed -n 's/^blob //p' |
  sort -rn -k2 |
  head -10

# Analyze pack files
git verify-pack -v .git/objects/pack/*.idx |
  sort -k 3 -n |
  tail -10
```

### Clone Performance
```bash
# Analyze fetch performance
GIT_TRACE=1 git fetch origin

# Check pack statistics
git count-objects -vH

# Optimize repository
git gc --aggressive --prune=now
```

## 🎯 Investigation Workflows

### Bug Investigation Workflow
```bash
# 1. Find potential commits
git log -S"bug_pattern" --since="1 month ago"

# 2. Create investigation branch
git switch -c investigation/bug-123

# 3. Analyze changes
git log -p --since="1 month ago" -- **/relevant_files/*

# 4. Test specific commits
git checkout -b test/bug-123 suspect_commit
```

### Performance Regression Workflow
```bash
# 1. Create performance test
cat > perf-test.sh << 'EOF'
#!/bin/bash
time ./app benchmark
EOF
chmod +x perf-test.sh

# 2. Run bisect with performance test
git bisect start HEAD last_known_good
git bisect run ./perf-test.sh

# 3. Analyze results
git bisect log > performance-investigation.log
```

### Security Audit Workflow
```bash
# 1. Search for sensitive data
git log -p | grep -i "password\|secret\|key"

# 2. Check file permissions
git ls-files --stage | grep "100755"

# 3. Review auth changes
git log -p -- **/auth/** **/security/**

# 4. Generate security report
git log --since="1 month ago" --grep="security" --pretty=format:"%h - %s" > security-audit.log
``` 