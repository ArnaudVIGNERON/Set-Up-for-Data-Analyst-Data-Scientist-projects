---
title: 06 - Version Control with Git
author: Arnaud Vigneron
date: 2026-07-24
tags:
  - git
  - github
  - collaboration
---

# 06 - Version Control with Git

## Goal

In this chapter, we'll learn how Git helps us track changes, collaborate with other people, and maintain a complete history of a project.

We'll focus on the Git commands you'll use most often during day-to-day development.

## Prerequisites

Before starting this chapter, you should already have a Python project created and be comfortable working with it.

If not, Chapters 03 to 05 introduce the workflow used throughout this guide.

## Learning objectives

After completing this chapter, you'll be able to:

- understand the purpose of Git
- create meaningful commits
- retrieve changes from a remote repository
- publish your own changes
- follow a simple Git workflow

---

## Why this matters

Code evolves over time.

New features are added, bugs are fixed, analyses change, and projects are often developed by several people.

Git records these changes and allows the entire team to work on the same project while keeping a complete history of what has changed.

Rather than thinking of Git as a backup tool, it's more helpful to think of it as the history of your project.

---

## The Git workflow

Throughout this guide, we'll use a simple Git workflow.

```text
Modify files
      │
      ▼
Check the changes
      │
      ▼
Create a commit
      │
      ▼
Push the commit
      │
      ▼
Share the changes
```

We'll now look at each step individually.

---

## Checking your changes

Before creating a commit, it's a good habit to check what has changed.

```powershell
git status
```

This command shows:

- modified files
- newly created files
- deleted files
- files that haven't yet been added to the next commit

Running `git status` regularly helps avoid accidentally committing files that weren't intended to be part of the change.

---

## Creating a commit

Once you're happy with your changes, stage them with:

```powershell
git add .
```

Then create a commit.

```powershell
git commit -m "Add customer segmentation analysis"
```

A commit represents a checkpoint in the history of the project.

Choose commit messages that describe **what** changed.

Good examples:

- Add monthly sales dashboard
- Fix incorrect revenue calculation
- Update project documentation

Less helpful examples:

- Update
- Changes
- Fix

---

## Synchronizing with GitHub

Once you've committed your changes, you can publish them to the remote repository.

Retrieve any new changes:

```powershell
git pull
```

Then publish your own work:

```powershell
git push
```

When working as part of a team, it's a good habit to pull changes before starting work and push your own commits once they're ready to share.

---

## Summary

Git records the history of a project and makes collaboration easier.

Throughout this guide, we'll use a simple workflow:

- check your changes
- create a commit
- pull remote changes
- push your work

Following the same workflow across projects helps keep the project's history clean and easy to understand.

---

## After completing this chapter

You should now be able to:

- understand the purpose of Git
- inspect the status of a project
- create meaningful commits
- synchronize with a remote repository
- follow a simple Git workflow

---

## Cheat Sheet

| Task | Command |
|------|---------|
| Check project status | `git status` |
| Stage all changes | `git add .` |
| Create a commit | `git commit -m "Message"` |
| Retrieve remote changes | `git pull` |
| Publish local commits | `git push` |
