---
title: 08 - Troubleshooting
author: Arnaud Vigneron
date: 2026-07-24
tags:
  - troubleshooting
  - python
  - uv
  - pyenv
  - vscode
---

# 08 - Troubleshooting

## Goal

In this chapter, we'll look at some of the most common issues you may encounter while working with Python, `uv`, Git, and Visual Studio Code.

Rather than trying to cover every possible error, this chapter focuses on the situations that are most likely to happen during onboarding.

## Learning objectives

After completing this chapter, you'll be able to:

- identify common setup issues
- resolve the most frequent Python environment problems
- understand where to look when something doesn't work
- know when it's time to ask for help

---

## Why this matters

Running into problems is a normal part of software development.

Even experienced developers regularly encounter configuration issues, dependency conflicts, or unexpected errors.

The important part isn't avoiding every problem—it's learning how to identify them and resolve them methodically.

---

## Visual Studio Code is using the wrong Python interpreter

Symptoms:

- packages appear to be missing
- imports are highlighted as errors
- the wrong Python version is displayed

Solution:

Select the project's interpreter.

Open the Command Palette.

```text
Ctrl + Shift + P
```

Search for:

```text
Python: Select Interpreter
```

Then select the interpreter located inside:

```text
.venv/Scripts/python.exe
```

Most interpreter-related issues are resolved by selecting the correct virtual environment.

---

## A package cannot be imported

If Python reports that a package cannot be imported, first synchronize the project's environment.

```powershell
uv sync
```

If the package is still missing, verify that it exists in `pyproject.toml`.

Avoid installing packages manually with `pip`, as this bypasses the project's dependency management.

---

## The wrong Python version is being used

Check the current version.

```powershell
python --version
```

List the installed Python versions.

```powershell
pyenv versions
```

If necessary, select the version used by the project.

```powershell
pyenv local 3.13.7
```

Restart Visual Studio Code if the interpreter doesn't update automatically.

---

## PowerShell blocks Python commands

If you see an error mentioning the PowerShell execution policy, allow locally created scripts.

```powershell
Set-ExecutionPolicy -Scope CurrentUser RemoteSigned
```

This only changes the execution policy for your own user account.

---

## I'm not sure what's wrong

When something doesn't work, try answering these questions:

- Am I inside the correct project folder?
- Is the virtual environment synchronized?
- Is Visual Studio Code using the correct interpreter?
- Am I using the correct Python version?
- Have I restarted the terminal after changing the configuration?

Working through these questions often helps identify the source of the problem before looking for more advanced solutions.

If you're still unable to resolve the issue, don't hesitate to ask a teammate for help.

Sometimes a second pair of eyes is the quickest solution.

---

## Summary

Most issues encountered during development are related to configuration rather than Python itself.

Understanding how Python versions, virtual environments, and project dependencies work makes these problems much easier to resolve.

Over time, troubleshooting becomes another part of your normal development workflow.

---

## Cheat Sheet

| Problem | First thing to check |
|---------|----------------------|
| Import error | `uv sync` |
| Wrong Python version | `python --version` |
| Wrong interpreter | Select `.venv` in VS Code |
| PowerShell error | Execution policy |
| Git issue | `git status` |
