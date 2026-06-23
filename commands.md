# Git & GitHub Notes

## Configuring Git

```bash
git config --global user.name "My Name"
git config --global user.email "someone@gmail.com"
git config --list
```

* `user.name` → Sets your Git username.
* `user.email` → Sets your Git email.
* `git config --list` → Displays all Git configurations.

---

# Clone & Status

## Clone

Clone a repository to your local machine:

```bash
git clone <repository-link>
```

## Status

Displays the current status of your repository:

```bash
git status
```

Possible file states:

* **Untracked** → New files that Git is not tracking yet.
* **Modified** → Existing files that have been changed.
* **Staged** → Files that have been added and are ready to commit.
* **Unmodified** → Files that have not changed.

---

# Add & Commit

## Add

Adds new or modified files to the staging area:

```bash
git add <file-name>
```

Add all files:

```bash
git add .
```

## Commit

Records the staged changes in the repository history:

```bash
git commit -m "Commit message"
```

---

# Push

Uploads local commits to a remote repository:

```bash
git push origin main
```

* `origin` → Remote repository alias.
* `main` → Branch being pushed.

Set the upstream branch:

```bash
git push -u origin main
-u sets origin main to default therefore wont have to type it again and again, git push will suffice
```

After this, future pushes can often be done using:

```bash
git push
```

---

# Initialize a Repository

Create a new Git repository locally:

```bash
git init
```

Connect it to GitHub:

```bash
git remote add origin <repository-link>
git remote -v
```

Rename current branch to main:

```bash
git branch -M main
```

Push for the first time:

```bash
git push -u origin main
```

---

# Branch Commands

View branches:

```bash
git branch
```

Create a new branch:

```bash
git branch <branch-name>
```

or

```bash
git checkout -b <branch-name>
```

or

```bash
git switch -c <branch-name>
```

Switch branches:

```bash
git checkout <branch-name>
```

or

```bash
git switch <branch-name>
```

Rename current branch:

```bash
git branch -m <new-branch-name>
```

Delete a branch:

```bash
git branch -d <branch-name>
```

---

# Comparing Changes

Compare your current branch with another branch:

```bash
git diff <branch-name>
```

Examples:

```bash
git diff main
git diff feature
```

---

# Merging Code

Merge another branch into the current branch:

```bash
git merge <branch-name>
```

Important Rule:

> `git merge X` means "merge branch X into the branch I am currently on."

Example:

```bash
git switch main
git merge feature
```

This merges `feature` into `main`.

---

# Pull Requests (PR)

A Pull Request (PR) is a GitHub feature that allows you to request that your changes be reviewed and merged into another branch.

Typical workflow:

```text
Create Branch
      ↓
Make Changes
      ↓
Commit
      ↓
Push
      ↓
Open Pull Request
      ↓
Review
      ↓
Merge
```

PRs are commonly used in team projects and open-source development.

---

# Pull

Fetches and downloads content from a remote repository and immediately updates the local branch:

```bash
git pull origin main
```

Equivalent to:

```bash
git fetch
git merge
```

---

# Merge Conflicts

A merge conflict occurs when Git cannot automatically determine which changes should be kept while merging.

Git will ask you to manually resolve the conflicting code before completing the merge.

---

# Undoing Changes

## Case 1: Undo Staged Changes

Remove files from the staging area:

```bash
git reset <file-name>
```

Remove all staged files:

```bash
git reset
```

---

## Case 2: Undo the Last Commit

```bash
git reset HEAD~1
```

Moves back one commit while keeping file changes.

---

## Case 3: Undo Multiple Commits

Reset to a specific commit:

```bash
git reset <commit-hash>
```

Discard all changes and reset completely:

```bash
git reset --hard <commit-hash>
```

Warning: `--hard` permanently removes uncommitted changes.

---

# View Commit History

View commit logs:

```bash
git log
```

Compact view:

```bash
git log --oneline
```

---

# Fork

A fork is a copy of another user's repository created under your own GitHub account.

Purpose:

* Experiment without affecting the original project.
* Contribute to open-source projects.
* Maintain your own version of a project.

Typical fork workflow:

```text
Original Repository
        ↓
       Fork
        ↓
      Clone
        ↓
   Create Branch
        ↓
   Make Changes
        ↓
      Commit
        ↓
       Push
        ↓
  Pull Request
        ↓
      Merge
```

Remote naming convention:

```text
origin   → Your fork
upstream → Original repository
```

Example:

```bash
git remote add upstream <original-repository-link>
```

---

# Contributors

A contributor is anyone whose changes have been merged into a repository.

Contributions can include:

* Bug fixes
* New features
* Documentation updates
* README improvements
* Tests
* Code refactoring
* Translations

Typical contribution process:

```text
Fork
 ↓
Branch
 ↓
Commit
 ↓
Push
 ↓
Pull Request
 ↓
Merge
```

Once your Pull Request is merged, you become a contributor to that repository.

---

# Useful Workflow

```bash
git status
git add .
git commit -m "Meaningful message"
git push
```

For collaborative projects:

```bash
git switch -c feature-branch
git add .
git commit -m "Added feature"
git push origin feature-branch
```

Then open a Pull Request on GitHub.


# Git Fetch

Downloads the latest changes from a remote repository **without merging them** into the current branch.

## Syntax

```bash
git fetch <alias>
```

## Example

Current state:

```text
GitHub (origin/main)
A --- B --- C --- D

Local main
A --- B --- C
```

Download new changes:

```bash
git fetch origin
```

Git now knows about commit `D`, but your local branch remains unchanged.

View the changes:

```bash
git log origin/main --oneline
git diff main origin/main
```

Merge when ready:

```bash
git merge origin/main
```

## Memory Trick

```text
fetch = download only
pull  = download + merge
```

---

# Git Rebase

Reapplies the current branch's commits on top of another branch, creating a cleaner linear history.

## Syntax

```bash
git rebase <branch>
```

## Example

Before:

```text
A --- B --- C  main
      \
       D --- E  feature
```

Run:

```bash
git switch feature
git rebase main
```

After:

```text
A --- B --- C --- D' --- E'  feature
```

Git moves the feature commits to the tip of `main`.

## Memory Trick

```text
merge  = combine histories
rebase = move my commits on top
```

---

# Git Stash

Temporarily saves uncommitted changes and restores the working directory to a clean state.

## Syntax

```bash
git stash
```

## Example

You are working on:

```text
commands.md
index.html
```

but need to switch branches.

Save your work:

```bash
git stash
```

Switch branches:

```bash
git switch main
```

Restore your work later:

```bash
git switch feature
git stash pop
```

Your changes return exactly as they were before.

## Useful Commands

```bash
git stash
git stash list
git stash apply
git stash pop
git stash drop
git stash clear
```

## Memory Trick

```text
commit = save permanently

stash = save temporarily
```
