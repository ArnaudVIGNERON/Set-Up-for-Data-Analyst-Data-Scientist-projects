---
title: 05 - Daily Workflow
author: Arnaud Vigneron
date: 2026-07-24
tags:
  - python
  - uv
  - vscode
  - workflow
---

# 05 - Working on a Project Every Day

## Goal

In this chapter, we'll look at the workflow you'll use most often when working on a Python project.

Rather than introducing new tools, we'll focus on the habits that help keep projects consistent, reproducible, and easy to maintain.

## Prerequisites

Before starting this chapter, you should already have a Python project created and understand how dependencies are managed with `uv`.

If not, Chapters 03 and 04 cover these topics.

## Learning objectives

After completing this chapter, you'll be able to:

- start working on an existing project
- keep your virtual environment synchronized
- add new dependencies when needed
- run Python scripts and Jupyter notebooks
- recognize a typical daily workflow

---

## Why this matters

Most of your time won't be spent creating new projects.

Instead, you'll spend it returning to existing ones, analysing new datasets, fixing issues, adding features, and collaborating with other people.

Having a consistent workflow makes it easier to move between projects and reduces the amount of time spent thinking about your development environment.

---

## Opening an existing project

Begin by opening a PowerShell terminal and navigating to your project.

```powershell
cd C:\Python_Projects\sales-analysis
```

Before starting work, synchronize the project's virtual environment.

```powershell
uv sync
```

If new dependencies have been added since you last worked on the project, `uv` will install them automatically.

Once the environment is ready, open the project in Visual Studio Code.

```powershell
code .
```

The workflow is summarized below.

```text
Open PowerShell
        │
        ▼
Navigate to the project
        │
        ▼
      uv sync
        │
        ▼
      code .
        │
        ▼
Start working
```

This simple routine ensures that you're always working with the correct environment before writing or running code.

---

## Working with notebooks and scripts

During a project, you'll often switch between exploratory analysis and Python scripts.

Jupyter notebooks are well suited for:

- exploring new datasets
- testing ideas
- creating visualizations
- documenting analyses

Python scripts are better suited for:

- reusable code
- automation
- data pipelines
- functions that will be used repeatedly

It's common for a project to contain both notebooks and Python files.

As the project grows, code developed in notebooks can gradually be moved into Python modules when it becomes reusable.

---

## Adding a new dependency

It's common to discover that a project needs an additional library.

For example, you may decide to create visualizations with `seaborn`.

Simply add the package to the project.

```powershell
uv add seaborn
```

Once the command finishes, the package is immediately available throughout the project's virtual environment.

Because `uv` updates the project configuration automatically, anyone else working on the project can install the same dependency by running `uv sync`.

---

## Summary

Most days, working on a Python project follows a simple routine.

Open the project, synchronize the environment, and start working.

Whenever new dependencies are needed, add them with `uv` rather than installing them manually.

Following the same workflow across projects helps keep development environments consistent and makes collaboration much easier.

---

## After completing this chapter

You should now be able to:

- open an existing Python project
- synchronize the project's environment
- add new dependencies when needed
- decide when to use notebooks or Python scripts
- follow a consistent daily workflow

---

## Cheat Sheet

| Task | Command |
|------|---------|
| Open a project | `cd C:\Python_Projects\sales-analysis` |
| Synchronize dependencies | `uv sync` |
| Open Visual Studio Code | `code .` |
| Add a dependency | `uv add <package>` |
| Run a Python script | `python main.py` |
| Start Jupyter | `jupyter lab` |
