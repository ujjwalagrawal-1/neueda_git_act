
# Yit : Your Cook 

Imagine building a LEGO house and taking a photo after every change.  
If someone breaks it, you can rebuild it exactly from the photos.

That's what **Git** does for your code.

---

## What is Git?

**Git** is a free, fast, open-source **Version Control System (VCS)**.

It helps you:

- Track code history over time
- Collaborate with teammates
- Restore previous versions when things go wrong

---

## Core Git Concepts

### 1) Repository (Repo)

A **repository** is your project folder where Git tracks all changes.

```bash
git init
```

**What `git init` does:**

- Creates a hidden `.git` folder in your project
- This folder stores all version history and commits
- Transforms a normal folder into a Git repository
- Only needs to be run **once per project**

---

### 2) The Three States of Git

```
Working Directory  →  Staging Area  →  Repository
   (modified)          (staged)         (committed)
```

#### 📁 Working Directory
Where you edit files. Changes are **untracked** until you stage them.

#### 📦 Staging Area
Files ready to be committed.

```bash
git add filename.txt        # Stage specific file
git add .                   # Stage all changes
```

#### 🗄️ Repository
Where Git permanently stores your commits.

```bash
git commit -m "your message"
```

---

## Basic Git Workflow

### Step 1: Check Status

```bash
git status
```

Shows what files are modified, staged, or untracked.

---

### Step 2: Stage Your Changes

```bash
git add .                   # Stage all changes
git add filename.txt        # Stage specific file
```

**Undo staging:**

```bash
git restore --staged filename.txt    # Unstage a file
```

---

### Step 3: Commit Your Changes

```bash
git commit -m "feat: add login feature"
```

**Undo last commit (keep changes):**

```bash
git reset HEAD~1
```

---

### Step 4: Push to GitHub

```bash
git push origin main
```

---

## Understanding Key Commands

### `git pull` vs `git fetch`

#### `git fetch`
Downloads updates from remote but **doesn't merge** them.

```bash
git fetch origin
```

You can review changes before merging.

#### `git pull`
**Shortcut** for `git fetch` + `git merge`.

```bash
git pull origin main
```

**Use this most of the time** to get latest changes.

---

### `git merge` vs `git rebase`

#### `git merge`
Combines branches, keeps all history.

```
Before:
       C---D (feature)
      /
 A---B---E (main)

After merge:
       C---D
      /     \
 A---B---E---F (merge commit)
```

```bash
git checkout main
git merge feature-branch
```

#### `git rebase`
Creates clean, linear history.

```
Before:
       C---D (feature)
      /
 A---B---E (main)

After rebase:
 A---B---E---C'---D' (clean line)
```

```bash
git checkout feature-branch
git rebase main
```

**⚠️ Rule:** Only rebase your own local branches, never shared ones.

---

## Branching: Work Safely

Create a new branch to try features without breaking main code.

```bash
git branch                      # See all branches
git checkout -b feature-name    # Create and switch to new branch
git checkout main               # Switch back to main
git merge feature-name          # Merge feature into main
git branch -d feature-name      # Delete branch after merge
```

---

## First Time on a New Repo? Run These

### 1) Check Where You Are

```bash
git branch                  # See current branch
git status                  # See uncommitted changes
```

### 2) See Recent Work

```bash
git log --oneline -10       # Last 10 commits
```

### 3) Get Latest Changes

```bash
git pull origin main
```

### 4) Check Remote Connection

```bash
git remote -v
```

Shows your GitHub URL.

---

## Common Mistakes & Quick Fixes

### ❌ Mistake 1: Wrong Commit Message

```bash
git commit --amend -m "correct message"
```

---

### ❌ Mistake 2: Want to Undo Changes (Before Commit)

```bash
git restore filename.txt        # Discard changes in one file
git restore .                   # Discard all changes
```

---

### ❌ Mistake 3: Committed by Mistake

```bash
git reset HEAD~1                # Undo commit, keep changes
```

---

### ❌ Mistake 4: Accidentally Added Wrong Files

```bash
git restore --staged filename.txt    # Unstage file
```

---

### ❌ Mistake 5: Merge Conflicts

**What it looks like:**

```
<<<<<<< HEAD
Your code
=======
Their code
>>>>>>> branch-name
```

**How to fix:**

1. Open the file
2. Keep the code you want
3. Delete the markers (`<<<<<<<`, `=======`, `>>>>>>>`)
4. Save and commit:

```bash
git add filename.txt
git commit -m "resolve conflict"
```

---

### ❌ Mistake 6: Need to Remove File from Git (but keep locally)

```bash
git rm --cached filename.txt
git commit -m "remove from git"
```

---

## Writing Good Commit Messages

### ❌ Bad

```bash
git commit -m "fixed stuff"
```

### ✅ Good

```bash
git commit -m "fix(auth): resolve login crash on invalid password"
```

### Format

```
<type>(<area>): <what you did>
```

### Common Types

| Type | When to Use |
|------|-------------|
| `feat` | New feature |
| `fix` | Bug fix |
| `docs` | Documentation only |
| `refactor` | Code cleanup |
| `chore` | Config/setup changes |

### Example

```
feat: add user profile page

Created new profile component with avatar upload.
Connected to /api/user endpoint.

Closes #42
```

---

## Connecting to GitHub

### First Time Setup

```bash
git remote add origin https://github.com/username/repo.git
git branch -M main
git push -u origin main
```

### Daily Workflow

```bash
git pull origin main            # Get latest changes
# ... make your changes ...
git add .
git commit -m "your message"
git push origin main            # Upload changes
```

---

## Essential Commands Cheat Sheet

### Setup
```bash
git init                        # Start tracking
git clone <url>                 # Copy repo from GitHub
```

### Daily Use
```bash
git status                      # Check what changed
git add .                       # Stage changes
git commit -m "message"         # Save changes
git push                        # Upload to GitHub
git pull                        # Download from GitHub
```

### Branching
```bash
git branch                      # List branches
git checkout -b new-feature     # Create new branch
git checkout main               # Switch to main
git merge feature-branch        # Combine branches
```

### Checking
```bash
git log --oneline               # See commit history
git diff                        # See what changed
```

### Undo
```bash
git restore file.txt            # Discard changes
git restore --staged file.txt   # Unstage
git reset HEAD~1                # Undo last commit
```

---

## Why Git Matters

✅ Undo mistakes easily  
✅ Collaborate without conflicts  
✅ Never lose your work  
✅ Required by most employers  
✅ Makes you look professional  

---

## Final Thoughts

**Master these 5 commands first:**

```bash
git status      # Check state
git add .       # Stage files
git commit      # Save checkpoint
git push        # Upload
git pull        # Download
```

Everything else builds on this foundation.

Don't try to memorize everything.  
**Understand the flow:**

```
Edit → Stage → Commit → Push
```

The rest comes with practice. 🚀