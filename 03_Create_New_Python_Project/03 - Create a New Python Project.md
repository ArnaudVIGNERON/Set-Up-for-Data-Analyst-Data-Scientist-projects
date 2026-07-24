---
title: 03 - Create a New Python Project
author: Arnaud Vigneron
date: 2026-07-24
tags:
  - python
  - tutorial
  - git
  - pyenv
  - uv
  - VS Code
---

# Part 3 — Create a New Python Project

Create the folder:

```powershell
mkdir sales-analysis
cd sales-analysis
```

Initialize Git:

```powershell
git init
```

Set the Python version for this project:

```powershell
pyenv local 3.13.7
```

This creates:

```text
.python-version
```

Initialize the uv project:

```powershell
uv init
```

Create the virtual environment:

```powershell
uv venv
```

Activate it:

```powershell
.venv\Scripts\Activate.ps1
```

Install common data analysis packages:

```powershell
uv add pandas numpy matplotlib seaborn jupyter
```

Open VS Code:

```powershell
code .
```
