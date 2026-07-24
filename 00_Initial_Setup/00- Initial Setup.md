---
title: 00 - Initial Setup
author: Arnaud Vigneron
date: 2026-07-24
tags:
  - python
  - tutorial
  - uv
  - pyenv
  - VS code
  - winget
---

# Part 0 — Initial Setup

## 1. Install winget

'winget' is the Windows package manager. It lets us install tools from PowerShell.

Check if it is installed:

```powershell
winget --version
```

If this returns a version number, continue.


## 2. Install Git

Git tracks changes in your code.

Install Git:

```powershell
winget install --id Git.Git --exact
```

Close and reopen PowerShell.

Verify:

```powershell
git --version
```

Configure your identity:

```powershell
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

Verify:

```powershell
git config --list
```

---

## 3. Install pyenv-win

`pyenv-win` lets you install and switch between multiple Python versions.

Install manually with Git:

```powershell
mkdir "$env:USERPROFILE\.pyenv"

git clone https://github.com/pyenv-win/pyenv-win.git "$env:USERPROFILE\.pyenv\pyenv-win"
```

If your folder ends up nested like this:

```text
C:\Users\yourname\.pyenv\pyenv-win\pyenv-win
```

then use that as your pyenv root.

Set environment variables:

```powershell
$pyenvRoot = "$env:USERPROFILE\.pyenv\pyenv-win\pyenv-win"

[Environment]::SetEnvironmentVariable("PYENV", $pyenvRoot, "User")
[Environment]::SetEnvironmentVariable("PYENV_ROOT", $pyenvRoot, "User")
[Environment]::SetEnvironmentVariable("PYENV_HOME", $pyenvRoot, "User")
```

Add pyenv to PATH:

```powershell
$userPath = [Environment]::GetEnvironmentVariable("Path", "User")

$bin = "$pyenvRoot\bin"
$shims = "$pyenvRoot\shims"

if ($userPath -notlike "*$bin*") { $userPath = "$bin;$userPath" }
if ($userPath -notlike "*$shims*") { $userPath = "$shims;$userPath" }

[Environment]::SetEnvironmentVariable("Path", $userPath, "User")
```

Close and reopen PowerShell.

If PowerShell blocks pyenv scripts, run:

```powershell
Set-ExecutionPolicy -Scope CurrentUser RemoteSigned
```

Verify:

```powershell
pyenv --version
```

---

## 4. Install Python versions

Recommended versions:

```powershell
pyenv install 3.10.18
pyenv install 3.11.13
pyenv install 3.12.11
pyenv install 3.13.7
```

Set the default Python version:

```powershell
pyenv global 3.13.7
```

Verify:

```powershell
python --version
pyenv versions
```

---

## 5. Install uv

`uv` manages virtual environments and project dependencies.

Install:

```powershell
winget install --id astral-sh.uv --exact
```

Verify:

```powershell
uv --version
```

---

## 6. Install Visual Studio Code

Install VS Code:

```powershell
winget install --id Microsoft.VisualStudioCode --exact
```

Recommended extensions:

Essential:

* Python
* Pylance
* Ruff
* GitLens

Recommended:

* Jupyter
* Error Lens
* Even Better TOML
* Markdown All in One
* GitHub Pull Requests and Issues
