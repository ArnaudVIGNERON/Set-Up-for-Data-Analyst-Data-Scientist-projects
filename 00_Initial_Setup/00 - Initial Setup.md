---
title: 00 - Initial Setup
author: Arnaud Vigneron
date: 2026-07-24
tags:
  - python
  - onboarding
  - uv
  - pyenv
  - git
  - visual studio code
---

# 00 - Initial Setup

## Goal

In this chapter, we'll prepare your computer for Python development.

We'll install the tools used throughout this guide and verify that everything is working correctly before creating our first project.

## Learning objectives

After completing this chapter, you'll be able to:

- install the tools used throughout this guide
- verify that each tool is correctly configured
- understand the role of each tool in the development workflow
- prepare your computer for creating Python projects

---

## Why this matters

Setting up a development environment only has to be done once, but doing it carefully saves a lot of time later.

Throughout this guide, we'll use the same set of tools for every project. This ensures that projects are reproducible, easy to maintain, and easier to share with other developers.

The tools introduced in this chapter are widely used within the Python ecosystem and work well together.

---

## Tools used throughout this guide

| Tool | Purpose |
|------|---------|
| Git | Tracks changes and allows collaboration |
| pyenv-win | Installs and manages multiple Python versions |
| Python | Programming language used throughout the guide |
| uv | Creates virtual environments and manages project dependencies |
| Visual Studio Code | Code editor used throughout the guide |

Throughout the rest of this repository, we'll build on this environment rather than introducing additional tools.

---

# 1. Install winget

`winget` is the Windows package manager.

We'll use it to install most of the software required throughout this guide.

Check whether it is already installed.

```powershell
winget --version
```

If a version number is displayed, you can continue to the next step.

---

# 2. Install Git

Git records the history of your projects and makes collaboration much easier.

Install Git.

```powershell
winget install --id Git.Git --exact
```

Close and reopen PowerShell.

Verify the installation.

```powershell
git --version
```

Configure your identity.

```powershell
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

Verify the configuration.

```powershell
git config --list
```

---

# 3. Install pyenv-win

`pyenv-win` allows you to install and switch between multiple Python versions.

Create the installation directory.

```powershell
mkdir "$env:USERPROFILE\.pyenv"
```

Clone the repository.

```powershell
git clone https://github.com/pyenv-win/pyenv-win.git "$env:USERPROFILE\.pyenv\pyenv-win"
```

Depending on the installation, the final folder may be:

```text
C:\Users\<username>\.pyenv\pyenv-win\pyenv-win
```

If that's the case, use this folder as your `PYENV_ROOT`.

Configure the required environment variables.

```powershell
$pyenvRoot = "$env:USERPROFILE\.pyenv\pyenv-win\pyenv-win"

[Environment]::SetEnvironmentVariable("PYENV", $pyenvRoot, "User")
[Environment]::SetEnvironmentVariable("PYENV_ROOT", $pyenvRoot, "User")
[Environment]::SetEnvironmentVariable("PYENV_HOME", $pyenvRoot, "User")
```

Add `pyenv` to your `PATH`.

```powershell
$userPath = [Environment]::GetEnvironmentVariable("Path", "User")

$bin = "$pyenvRoot\bin"
$shims = "$pyenvRoot\shims"

if ($userPath -notlike "*$bin*") { $userPath = "$bin;$userPath" }
if ($userPath -notlike "*$shims*") { $userPath = "$shims;$userPath" }

[Environment]::SetEnvironmentVariable("Path", $userPath, "User")
```

Close and reopen PowerShell.

If PowerShell prevents `pyenv` from running, allow locally created scripts.

```powershell
Set-ExecutionPolicy -Scope CurrentUser RemoteSigned
```

Verify the installation.

```powershell
pyenv --version
```

---

# 4. Install Python

We'll install several Python versions.

Keeping multiple versions available makes it easier to work on projects with different requirements.

Install the recommended versions.

```powershell
pyenv install 3.10.18
pyenv install 3.11.13
pyenv install 3.12.11
pyenv install 3.13.7
```

Set the default version.

```powershell
pyenv global 3.13.7
```

Verify the installation.

```powershell
python --version
```

List all installed versions.

```powershell
pyenv versions
```

---

# 5. Install uv

`uv` is responsible for creating virtual environments and managing project dependencies.

Install it with `winget`.

```powershell
winget install --id astral-sh.uv --exact
```

Verify the installation.

```powershell
uv --version
```

---

# 6. Install Visual Studio Code

Install Visual Studio Code.

```powershell
winget install --id Microsoft.VisualStudioCode --exact
```

Install the following extensions.

### Essential

- Python
- Pylance
- Ruff
- GitLens

### Recommended

- Jupyter
- Error Lens
- Even Better TOML
- Markdown All in One
- GitHub Pull Requests and Issues

We'll configure Visual Studio Code in the next chapter.

---

## Summary

In this chapter, we've prepared the development environment used throughout the guide.

We've installed:

- Git
- pyenv-win
- Python
- uv
- Visual Studio Code

Your computer is now ready to create and work on Python projects.

---

## After completing this chapter

You should now be able to:

- install the tools used throughout this guide
- verify that each tool is correctly installed
- understand the purpose of each tool
- begin creating Python projects
