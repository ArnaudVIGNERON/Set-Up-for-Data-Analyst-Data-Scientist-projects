---
title: 07 - Troubleshooting
author: Arnaud Vigneron
date: 2026-07-24
tags:
  - tutorial
  - uv
  - pyenv
  - VS Code
---

# Part 7 — Troubleshooting

## pyenv is not recognized

Error:

```text
pyenv is not recognized
```

Check where pyenv is installed:

```powershell
Get-ChildItem "$env:USERPROFILE" -Recurse -Filter pyenv.bat -ErrorAction SilentlyContinue | Select-Object FullName
```

Then ensure these folders are in your user PATH:

```text
...\pyenv-win\bin
...\pyenv-win\shims
```

Close and reopen PowerShell.

---

## PowerShell blocks pyenv

Error:

```text
running scripts is disabled on this system
```

Fix:

```powershell
Set-ExecutionPolicy -Scope CurrentUser RemoteSigned
```

---

## Python version does not change

Run:

```powershell
pyenv version
pyenv versions
where.exe python
```

If Windows Store Python appears first, disable Python aliases:

```text
Settings
→ Apps
→ Advanced app settings
→ App execution aliases
→ Disable python.exe and python3.exe
```

---

## VS Code uses the wrong Python

In VS Code:

```text
Ctrl + Shift + P
Python: Select Interpreter
```

Choose:

```text
.venv\Scripts\python.exe
```

---

## Virtual environment activation fails

If activation is blocked:

```powershell
Set-ExecutionPolicy -Scope CurrentUser RemoteSigned
```

Then try again:

```powershell
.venv\Scripts\Activate.ps1
```

---

## Package installed but not found

Make sure the correct environment is active:

```powershell
where.exe python
python --version
uv pip list
```

If needed:

```powershell
uv sync
```
