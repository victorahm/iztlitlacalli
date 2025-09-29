# Git Branch Management

## 📋 Overview
Essential Git commands for creating, switching, merging, and deleting branches in a Git repository.

## 🎯 Purpose
Manage parallel development lines, feature development, and maintain clean project history through proper branch management.

## 💡 Implementation

### Basic Branch Operations
```bash
# List all branches
git branch                    # Local branches
git branch -r                 # Remote branches  
git branch -a                 # All branches

# Create a new branch
git branch feature-name       # Create but don't switch
git checkout -b feature-name  # Create and switch
git switch -c feature-name    # Modern alternative

# Switch between branches
git checkout branch-name      # Traditional way
git switch branch-name        # Modern alternative

# Rename a branch
git branch -m old-name new-name

# Delete a branch
git branch -d branch-name     # Safe delete (merged only)
git branch -D branch-name     # Force delete
```

### Merging and Integration
```bash
# Merge a branch into current branch
git merge feature-branch

# Create a merge commit even for fast-forward
git merge --no-ff feature-branch

# Rebase current branch onto another
git rebase main

# Interactive rebase for cleaning history
git rebase -i HEAD~3
```

## 🔍 Key Points
- Always create feature branches from an updated main/master
- Use descriptive branch names (feature/user-auth, bugfix/login-error)
- Delete merged branches to keep repository clean
- Consider using conventional branch naming patterns
- Prefer `git switch` and `git restore` over `git checkout` for clarity

## 🔗 Related Topics
- [[Programming/Git/Merge Strategies]]
- [[Programming/Git/Rebasing Guide]]
- [[Programming/Git/Remote Repositories]]

## 📚 References
- [Git Branching Documentation](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell)

## 🏷️ Tags
`#git` `#version-control` `#branching` `#workflow`

---
*Created: 2024-01-15 | Last Updated: 2024-01-15*