# .gitignore Guide

## 📝 What is .gitignore?

A `.gitignore` file tells Git which files or folders to ignore in a project. This is especially useful for:
- Build outputs
- Dependencies
- Local configuration files
- System files
- Personal IDE settings

## 🔧 Basic Syntax

### Common Patterns
```gitignore
# Ignore specific file
config.json

# Ignore file type
*.log

# Ignore directory
node_modules/
build/

# Ignore files in any directory with this name
**/temp/
```

### Advanced Patterns
```gitignore
# Negate pattern (include file)
*.log
!important.log

# Match single character
file?.txt

# Match character range
[0-9].txt

# Match any depth
**/logs
```

## 📚 Common Examples

### Node.js Project
```gitignore
# Dependencies
node_modules/
npm-debug.log
yarn-debug.log
yarn-error.log

# Environment
.env
.env.local

# Build output
dist/
build/
```

### Python Project
```gitignore
# Virtual environment
venv/
env/
*.pyc
__pycache__/

# Distribution
dist/
build/
*.egg-info/
```

### Visual Studio Code
```gitignore
.vscode/*
!.vscode/settings.json
!.vscode/tasks.json
!.vscode/launch.json
!.vscode/extensions.json
```

## 🚀 Best Practices

1. **Create Early**: Add `.gitignore` when initializing repository
2. **Be Specific**: Avoid overly broad patterns
3. **Document**: Comment patterns for clarity
4. **Use Templates**: GitHub provides language-specific templates
5. **Keep Updated**: Modify as project evolves

## 🔍 Troubleshooting

### Already Tracked Files
```bash
# Remove tracked file and add to .gitignore
git rm --cached filename

# Remove tracked directory
git rm -r --cached directory/
```

### Check Ignored Status
```bash
# Check if file is ignored
git check-ignore -v filename

# List all ignored files
git status --ignored
```

## 📖 Additional Resources
- [GitHub's .gitignore templates](https://github.com/github/gitignore)
- [Git documentation on .gitignore](https://git-scm.com/docs/gitignore)