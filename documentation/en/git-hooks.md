# Git Hooks and Automation

## 🎣 Understanding Git Hooks

Git hooks are scripts that Git executes before or after events such as: commit, push, and receive.

## 📂 Hook Locations

```bash
# Local hooks directory
.git/hooks/

# Project-wide hooks (shared)
.git-templates/hooks/
```

## 🔄 Available Hooks

### Pre-Commit Hooks
```bash
#!/bin/sh
# .git/hooks/pre-commit

# Run linter
npm run lint

# Run tests
npm test

# Check for debugging statements
if grep -r "debugger\|console.log" ./src/; then
  echo "Error: Debugging statements found"
  exit 1
fi
```

### Commit-Msg Hooks
```bash
#!/bin/sh
# .git/hooks/commit-msg

# Enforce conventional commits
commit_msg=$(cat "$1")
if ! echo "$commit_msg" | grep -qE "^(feat|fix|docs|style|refactor|test|chore):"; then
  echo "Error: Commit message must follow conventional commits format"
  exit 1
fi
```

### Pre-Push Hooks
```bash
#!/bin/sh
# .git/hooks/pre-push

# Run full test suite
npm run test:full

# Check build
npm run build
```

## 🛠️ Common Use Cases

### Code Quality Checks
```bash
#!/bin/sh
# .git/hooks/pre-commit

# Check code formatting
prettier --check "src/**/*.{js,ts,jsx,tsx}"

# Run ESLint
eslint "src/**/*.{js,ts,jsx,tsx}"

# Check TypeScript types
tsc --noEmit
```

### Security Checks
```bash
#!/bin/sh
# .git/hooks/pre-commit

# Check for secrets
git secrets --scan

# Run security audit
npm audit

# Check dependencies
snyk test
```

### Automated Testing
```bash
#!/bin/sh
# .git/hooks/pre-push

# Run unit tests
jest

# Run integration tests
cypress run

# Check coverage
jest --coverage --coverageThreshold='{"global":{"branches":80}}'
```

## 📦 Setting Up Project-Wide Hooks

### Using Git Templates
```bash
# Create template directory
git config --global init.templateDir '~/.git-templates'
mkdir -p ~/.git-templates/hooks

# Add hooks to template
cp pre-commit ~/.git-templates/hooks/
chmod +x ~/.git-templates/hooks/pre-commit

# Initialize new repository with templates
git init
```

### Using Husky (Node.js)
```bash
# Install husky
npm install husky --save-dev

# Configure package.json
{
  "husky": {
    "hooks": {
      "pre-commit": "npm test",
      "pre-push": "npm run build"
    }
  }
}
```

## 🔧 Advanced Hook Techniques

### Skipping Hooks
```bash
# Skip pre-commit hooks
git commit --no-verify -m "Emergency fix"

# Skip pre-push hooks
git push --no-verify
```

### Sharing Hooks with Team
```bash
# Create hooks directory in project
mkdir .hooks

# Configure Git to use custom hooks path
git config core.hooksPath .hooks

# Add hooks to version control
git add .hooks
```

## 📝 Best Practices

1. Keep hooks fast and focused
2. Provide skip mechanisms for emergencies
3. Document hook requirements
4. Version control shared hooks
5. Use appropriate exit codes

## 🚀 Implementation Examples

### Conventional Commits Hook
```bash
#!/bin/sh
# .git/hooks/commit-msg

commit_msg_file=$1
commit_msg=$(cat "$commit_msg_file")

# Conventional commit pattern
pattern="^(feat|fix|docs|style|refactor|test|chore)(\(.+\))?: .{1,50}"

if ! echo "$commit_msg" | grep -qE "$pattern"; then
  echo "Error: Invalid commit message format."
  echo "Must follow: type(scope): message"
  echo "Types: feat, fix, docs, style, refactor, test, chore"
  exit 1
fi
```

### Code Quality Hook
```bash
#!/bin/sh
# .git/hooks/pre-commit

# Get staged files
files=$(git diff --cached --name-only --diff-filter=ACM | grep '\.jsx\?$')

# Exit if no JS files are staged
[ -z "$files" ] && exit 0

# Run prettier
echo "$files" | xargs prettier --write

# Run eslint
echo "$files" | xargs eslint --fix

# Add back the modified files
echo "$files" | xargs git add

exit 0
```

### Branch Naming Hook
```bash
#!/bin/sh
# .git/hooks/pre-commit

branch_name=$(git symbolic-ref --short HEAD)
valid_pattern="^(feature|bugfix|hotfix|release)/.+"

if ! echo "$branch_name" | grep -qE "$valid_pattern"; then
  echo "Error: Invalid branch name"
  echo "Must follow: type/description"
  echo "Types: feature, bugfix, hotfix, release"
  exit 1
fi
``` 