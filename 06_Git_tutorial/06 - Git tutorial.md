# Part 6 — Git Tutorial

## What is Git?

Git is a version control system.

It lets you:

* track changes
* undo mistakes
* create branches
* collaborate with others
* save project history

---

## Basic Git cycle

Most of the time, Git works like this:

```text
Edit files
   ↓
Check status
   ↓
Stage files
   ↓
Commit changes
   ↓
Push to GitHub
```

---

## Check project status

```powershell
git status
```

This shows which files changed.

---

## Pull latest changes

```powershell
git pull
```

Do this before starting work if others also work on the repository.

---

## Stage files

Stage all changes:

```powershell
git add .
```

Stage one file:

```powershell
git add README.md
```

---

## Commit changes

```powershell
git commit -m "Add initial project setup"
```

A good commit message should be short and clear.

Examples:

```text
Add sales cleaning script
Fix missing values in customer dataset
Update README with setup instructions
Add notebook for monthly analysis
```

---

## View history

```powershell
git log --oneline
```

---

## Create a branch

Branches let you work safely without changing the main version.

```powershell
git checkout -b feature/customer-cleaning
```

---

## Switch branches

```powershell
git checkout main
```

or:

```powershell
git switch main
```

---

## Merge a branch

```powershell
git checkout main
git merge feature/customer-cleaning
```

---

## Connect to GitHub

Create an empty repository on GitHub.

Then run:

```powershell
git remote add origin <repository-url>
git branch -M main
git push -u origin main
```

After that, future pushes are simply:

```powershell
git push
```

---
