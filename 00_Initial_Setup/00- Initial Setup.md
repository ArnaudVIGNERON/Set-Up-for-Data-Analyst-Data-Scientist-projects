---
title: 00 - Initial Setup
author: Arnaud Vigneron
date: 2026-07-24
tags:
  - python
  - tutorial
  - git
  - uv
  - pyenv
  - vscode
  - winget
---

# 00 — Initial Setup

## Goal

In this chapter, we will prepare your Windows computer for Python development.

We will install the tools used throughout this guide:

- Git
- pyenv-win
- Python
- uv
- Visual Studio Code

Do not worry if some of these tools are unfamiliar. We will introduce them one at a time and verify each installation before moving to the next one.

By the end of the chapter, your computer will be ready to create isolated, reproducible Python projects.

## Prerequisites

This guide assumes that you are using:

- Windows 11;
- PowerShell;
- a Windows user account that is allowed to install applications.

You do not need to open PowerShell as an administrator unless Windows specifically asks you to do so.

To open PowerShell:

1. Open the Windows Start menu.
2. Search for `PowerShell`.
3. Select **Windows PowerShell** or **PowerShell**.

---

## 1. Check WinGet

WinGet is the Windows package manager.

A package manager lets us install and update applications from the command line instead of downloading each installer manually.

Windows 11 normally includes WinGet through the **App Installer** application.

Check whether WinGet is available:

```powershell
winget --version
```

You should see a version number similar to:

```text
v1.x.x
```

The exact version may be different, which is perfectly fine.

If PowerShell tells you that `winget` is not recognised, install or update **App Installer** from the Microsoft Store before continuing.

---

## 2. Install Git

Git is a version-control system.

It records the history of a project and lets you:

- see which files changed;
- save meaningful versions of your work;
- return to an earlier version when necessary;
- work safely with branches;
- collaborate through platforms such as GitHub.

We will use Git throughout this guide, even when working alone. Starting with Git from the beginning is a useful habit because it gives every project a clear and recoverable history.

Install Git with WinGet:

```powershell
winget install --id Git.Git --exact --source winget
```

WinGet may ask you to accept source or package agreements. Read the prompt and confirm when you are ready.

After the installation finishes, close PowerShell completely and open a new PowerShell window. This allows Windows to refresh the commands available in your terminal.

### Verify Git

Run:

```powershell
git --version
```

You should see a result similar to:

```text
git version 2.x.x.windows.x
```

The exact version may be different.

### Configure your Git identity

Every Git commit records the name and email address of its author.

Replace the example values below with your own name and email address:

```powershell
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

Use the email address associated with your GitHub account when you want your commits to appear on your GitHub profile.

Verify the configuration:

```powershell
git config --global user.name
git config --global user.email
```

You should see the name and email address you entered.

> [!NOTE]
> The `--global` option applies this identity to all Git repositories used by your Windows account. A project can override it later when a different identity is required.

---

## 3. Install pyenv-win

Different Python projects may require different Python versions.

For example:

```text
Project A → Python 3.11
Project B → Python 3.12
Project C → Python 3.13
```

Installing and switching between these versions manually can quickly become confusing.

`pyenv-win` solves this problem on Windows. It lets us:

- install multiple Python versions;
- choose a default Python version;
- select a different Python version for an individual project.

In later chapters, each project will declare which Python version it expects.

### Install pyenv-win

Download and run the official PowerShell installer:

```powershell
Invoke-WebRequest `
    -UseBasicParsing `
    -Uri "https://raw.githubusercontent.com/pyenv-win/pyenv-win/master/pyenv-win/install-pyenv-win.ps1" `
    -OutFile "$env:TEMP\install-pyenv-win.ps1"

& "$env:TEMP\install-pyenv-win.ps1"
```

After the installation finishes, close every PowerShell window and open a new one.

This step is important because the installer updates your user environment variables and `PATH`.

### Verify pyenv-win

Run:

```powershell
pyenv --version
```

You should see the installed pyenv-win version.

You can also check where Windows found the command:

```powershell
where.exe pyenv
```

The returned path should point to a folder inside your Windows user profile.

### PowerShell execution policy

PowerShell may display an error saying that script execution is disabled.

In that case, allow locally installed scripts to run for your user account:

```powershell
Set-ExecutionPolicy -Scope CurrentUser RemoteSigned
```

Read the confirmation prompt and accept the change when you are ready.

Close and reopen PowerShell, then verify the installation again:

```powershell
pyenv --version
```

> [!NOTE]
> This setting applies only to your Windows user account. On a company-managed computer, an organisation-wide policy may prevent you from changing it. Contact your IT team when that happens.

---

## 4. Install Python

Now that pyenv-win is installed, we can use it to install Python.

### View available Python versions

Run:

```powershell
pyenv install --list
```

The list can be long. To display only regular Python 3.13 releases in PowerShell, run:

```powershell
pyenv install --list | Select-String "^\s*3\.13\.\d+\s*$"
```

You should see versions similar to:

```text
3.13.0
3.13.1
3.13.2
...
```

Choose the newest available patch release in the Python series used by your team or project.

The examples in this guide use **Python 3.13**. Replace `3.13.x` in the next commands with the exact version displayed on your computer.

For example, when the newest available release is `3.13.7`, run:

```powershell
pyenv install 3.13.7
```

> [!IMPORTANT]
> `3.13.x` is an example notation, not a command you should enter literally. Always use a complete version number such as `3.13.7`.

### Set the default Python version

After installing the version, set it as your global default:

```powershell
pyenv global 3.13.7
```

Replace `3.13.7` with the version you installed.

The global version is used whenever a project has not selected a different local version.

### Verify Python

Run:

```powershell
python --version
pyenv version
pyenv versions
```

You should see:

- the Python version currently in use;
- where pyenv selected that version;
- all Python versions installed through pyenv.

You can also check which Python executable Windows is using:

```powershell
where.exe python
```

The first result should normally point to the pyenv-win `shims` directory.

> [!NOTE]
> You do not need to install every available Python version now. Additional versions can be installed later when a project requires them.

---

## 5. Install uv

Python projects usually rely on external packages such as:

- `pandas`;
- `numpy`;
- `matplotlib`;
- `seaborn`;
- `pytest`;
- `ruff`.

We do not want to install all of these packages into one shared Python installation.

Instead, every project will have its own isolated environment and its own list of dependencies.

`uv` is the tool we will use to:

- create Python projects;
- create virtual environments;
- add and remove packages;
- record project dependencies;
- reproduce an environment on another computer;
- run commands inside the correct project environment.

We will explore these concepts in detail in the next chapter.

### Install uv

Install uv with WinGet:

```powershell
winget install --id astral-sh.uv --exact
```

Close and reopen PowerShell after the installation.

### Verify uv

Run:

```powershell
uv --version
```

You should see the installed uv version.

You can also check where Windows found it:

```powershell
where.exe uv
```

---

## 6. Install Visual Studio Code

Visual Studio Code, usually called **VS Code**, is the editor we will use to work with Python projects.

VS Code gives us one place to:

- write Python code;
- work with Jupyter notebooks;
- open a PowerShell terminal;
- run and debug programs;
- inspect Git changes;
- commit and push work to GitHub.

Install VS Code with WinGet:

```powershell
winget install --id Microsoft.VisualStudioCode --exact
```

After the installation finishes, close and reopen PowerShell.

### Verify VS Code

Run:

```powershell
code --version
```

You should see the installed VS Code version.

You can open VS Code from PowerShell with:

```powershell
code
```

Later, we will use the following command from inside a project folder:

```powershell
code .
```

The dot means “open the current folder in VS Code.”

---

## 7. Install the VS Code extensions

VS Code supports extensions that add features for particular programming languages and workflows.

Open VS Code and select the **Extensions** icon in the left sidebar. You can also open the Extensions view with:

```text
Ctrl + Shift + X
```

Search for and install the following extensions.

### Essential extensions

| Extension | Publisher | Purpose |
|---|---|---|
| Python | Microsoft | Runs, debugs, and manages Python projects |
| Pylance | Microsoft | Provides code completion, navigation, and type analysis |
| Ruff | Astral Software | Formats Python code and reports common code-quality issues |
| GitLens | GitKraken | Adds detailed Git history and change information |

### Recommended extensions

| Extension | Purpose |
|---|---|
| Jupyter | Opens and runs Jupyter notebooks |
| Error Lens | Displays errors and warnings directly beside the relevant code |
| Even Better TOML | Improves editing for files such as `pyproject.toml` |
| Markdown All in One | Adds useful tools for writing documentation and `README.md` files |
| GitHub Pull Requests | Adds GitHub pull-request and issue workflows to VS Code |

You do not need to configure these extensions yet.

In Chapter 02, we will configure VS Code and connect it to the virtual environment used by a Python project.

---

## 8. Final verification

Before moving on, open a new PowerShell window and run:

```powershell
winget --version
git --version
pyenv --version
python --version
uv --version
code --version
```

Every command should return a version number.

You can also run this diagnostic block:

```powershell
Write-Host "`nGit:"
where.exe git

Write-Host "`npyenv:"
where.exe pyenv

Write-Host "`nPython:"
where.exe python

Write-Host "`nuv:"
where.exe uv

Write-Host "`nVS Code:"
where.exe code
```

Do not worry if the displayed paths are different from another person's computer. Windows usernames and installation locations can vary.

What matters is that each command is recognised and points to the expected tool.

If one of the commands fails, stop here and consult the [Troubleshooting chapter](../07_Troubleshooting/07%20-%20Troubleshooting.md) before continuing.

---

## Common mistakes

### A newly installed command is not recognised

Windows may not have refreshed your `PATH` yet.

Close all PowerShell and VS Code windows, open a new PowerShell window, and try the command again.

### PowerShell blocks a script

Run:

```powershell
Set-ExecutionPolicy -Scope CurrentUser RemoteSigned
```

Then close and reopen PowerShell.

### The wrong Python installation is used

Check the available Python executables:

```powershell
where.exe python
```

The pyenv-win `shims` path should normally appear first.

If Windows displays a Microsoft Store alias before pyenv, open:

```text
Windows Settings
→ Apps
→ Advanced app settings
→ App execution aliases
```

Disable the aliases for:

```text
python.exe
python3.exe
```

Then close and reopen PowerShell.

### An installation is blocked on a managed computer

Company and school computers may restrict:

- application installation;
- PowerShell scripts;
- environment-variable changes;
- access to GitHub.

Do not try to bypass organisational security policies. Contact your IT team and provide them with the name of the tool you need.

---

## Summary

In this chapter, we installed the foundations of our Python development environment:

- WinGet installs and updates Windows applications.
- Git tracks the history of our projects.
- pyenv-win installs and selects Python versions.
- Python runs our code.
- uv manages project environments and dependencies.
- VS Code provides the workspace where we write, run, and review our work.

Each tool has a separate responsibility. Keeping those responsibilities clear will make the rest of the workflow much easier to understand.

---

## After completing this chapter

You should now be able to:

- open and use PowerShell;
- install applications with WinGet;
- verify whether a command is available;
- explain why Git is installed before creating a project;
- explain why pyenv-win manages Python versions;
- install and select a Python version with pyenv-win;
- explain the role uv will play in project dependency management;
- open Visual Studio Code;
- identify the VS Code extensions used throughout this guide.

---

## Next chapter

Now that the required tools are installed, the next step is to understand why every Python project should have its own isolated environment.

Continue with:

**[01 — Virtual Environments and Packages](../01_Virtual_Environments_and_Packages/01%20-%20Virtual%20Environments%20and%20Packages.md)**

---

## Official references

- [WinGet documentation](https://learn.microsoft.com/windows/package-manager/)
- [Git for Windows installation](https://git-scm.com/install/windows)
- [pyenv-win](https://github.com/pyenv-win/pyenv-win)
- [uv installation](https://docs.astral.sh/uv/getting-started/installation/)
- [Visual Studio Code on Windows](https://code.visualstudio.com/docs/setup/windows)
