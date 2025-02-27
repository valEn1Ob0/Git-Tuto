# Git Workflow Diagrams

## 🌳 Basic Branch Structure

```
main           ●─────●─────●─────●─────●
                     │     │     │
feature-1            ●─────●     │
                           │     │
feature-2                  ●─────●
```

## 🔄 Feature Branch Workflow

```
main        ●────●────●────●────●────● (v1.0)
                 │         │
feature-A        ●─────────●
                     │
feature-B            ●────●
```

## 📦 GitFlow Workflow

```
main          ●──────────────●──────────●  (v1.0)
                            │
develop     ●─●─●──────●────●──────●────●
              │      │    │      │
feature-1     ●──────●    │      │
                          │      │
feature-2                 ●──────●
```

## 🚀 Release Branch Flow

```
main          ●───────────●───────●  (v1.0)
                         │       │
release-1.0             ●───●───●
                           │
hotfix                    ●
```

## 🔀 Merge Strategies

### Fast-Forward Merge
```
main     ●────●────●────●
                   │
feature           ●────●
```

### Merge Commit
```
main     ●────●────●────●
                   │    │
feature           ●────●
```

### Rebase
```
Before:
main     ●────●────●
              │
feature        ●────●

After:
main     ●────●────●
                   │
feature           ●────●
```

## 🎯 Pull Request Flow

```
origin/main    ●────●────●────●
                    │
local/main     ●────●
                    │
feature        ●────●────●
                    │
PR                  ●─ → ─●
```

## 🔧 Conflict Resolution

```
main          ●────●────●
                   │ \
feature           ●──╳──●
                     │
resolved              ●
```

## 📈 Complex Workflow Example

```
main            ●──────────●──────────●  (v2.0)
                          │          │
release-2.0              ●──●───●────●
                           │   │
hotfix-2.0.1              ●   │
                              │
develop       ●─●─●──────●────●──────●
                │      │    │
feature-A       ●──────●    │
                           │
feature-B                  ●────●
```

## 🔄 Continuous Integration Flow

```
main          ●────●────●────●  (production)
               │    │    │
staging        ●────●────●      (staging)
               │    │
develop        ●────●           (development)
               │
feature        ●
```

## 🏷️ Tag and Release Strategy

```
main     ●─────●─────●─────●─────● (v1.0.0)
          │     │     │     │
tags     v0.1  v0.2  v0.3  v1.0-rc1
```

## 🔁 Fork and Sync Workflow

```
upstream/main    ●────●────●────●
                      │
origin/main      ●────●────●
                      │    │
local/feature         ●────●
```

## 📊 Branch Protection Rules

```
protected     ●──────●──────●  (requires review)
              │      │      │
feature-1     ●──────●      │
                           │
feature-2                  ●
```

## 🚦 Code Review Flow

```
main               ●────────●
                          │
feature       ●────●──────●
                  │
review-1          ●
                  │
review-2          ●
```

## 💡 Tips for Reading Diagrams

- ● represents a commit
- ─ represents branch timeline
- │ represents branch relationship
- → represents direction of operation
- ╳ represents conflict point

## 🎨 Common Patterns

### Topic Branches
```
main     ●────●────●────●
              │    │    │
topic-A       ●────●    │
                   │    │
topic-B            ●────●
```

### Long-Running Branches
```
main     ●────●────●────●  (stable)
              │
develop  ●────●────●────●  (integration)
              │    │
feature       ●────●      (temporary)
```

## 🔄 Advanced Workflow Patterns

### Trunk-Based Development
```
main     ●────●────●────●────●  (trunk)
          │    │    │    │
feature1  ●────●    │    │
               │    │    │
feature2       ●────●    │
                    │    │
feature3            ●────●
```

### Environment Branches
```
production    ●────●────●────●  (stable)
              │    │    │    │
staging       ●────●────●────●  (testing)
              │    │    │    │
development   ●────●────●────●  (integration)
              │    │    │    │
feature       ●────●    │    │
                   │    │    │
hotfix            ●────●────●
```

### Monorepo Strategy
```
main           ●───────●───────●
               │       │       │
service-a      ●───●───●       │
               │   │   │       │
service-b      ●───●   │       │
               │       │       │
shared-lib     ●───────●───────●
```

## 🎯 Feature Flag Workflow

### Feature Toggle Development
```
main          ●────●────●────●  (flag: off)
               │    │    │
feature-a      ●────●    │      (flag: on)
                    │    │
feature-b           ●────●      (flag: test)
```

### A/B Testing Flow
```
main          ●────●────●────●
               │         │
variant-a      ●─────────●     (50% users)
               │         │
variant-b      ●─────────●     (50% users)
```

## 🔀 Complex Merge Strategies

### Rebase and Merge
```
Before:
main     ●────●────●
              │
feature        ●────●

After:
main     ●────●────●────●
                        │
feature                 ●
```

### Squash and Rebase
```
Before:
main     ●────●────●
              │
feature        ●──●──●

After:
main     ●────●────●────●
```

## 🚀 Release Train Model

```
release-2.0    ●───────●───────●  (current)
                │       │
release-1.9     ●───────●         (maintenance)
                │       │
development     ●───●───●───●     (next)
                    │       │
features            ●───────●
```

## 📦 Dependency Management

### Submodule Workflow
```
main-project    ●────●────●────●
                │    │    │    │
module-a        ●────●    │    │
                     │    │    │
module-b            ●────●    │
                          │    │
module-c                 ●────●
```

### Composite Projects
```
meta-repo       ●────●────●────●
                │    │    │    │
project-a       ●────●    │    ├─────●
                │    │    │    │     │
project-b       ●────●────●    ├─────●
                │    │    │    │
project-c       ●────●────●────●
```

## 🔒 Security Patch Flow

```
main          ●────●────●────●────●  (public)
               │    │    │    │
security       ●────●────●────●      (private)
               │         │
hotfix         ●─────────●
```

## 🌐 Multi-Region Deployment

```
global        ●────●────●────●
              │    │    │    │
region-eu     ●────●────●    │
              │    │    │    │
region-us     ●────●────●────●
              │    │    │
region-asia   ●────●────●
```

## 🔄 Automated Backport Flow

```
main          ●────●────●────●  (2.0)
               │    │    │
backport-1.x   ●────●────●      (1.x)
               │    │
backport-0.x   ●────●           (0.x)
```

## 🎨 Design System Workflow

```
main           ●────●────●────●  (production)
                │    │    │
components      ●────●────●      (development)
                │    │
themes          ●────●
                │
documentation   ●
``` 