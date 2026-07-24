# Python Development Setup for Data Analysts

*A practical guide to building a modern, reproducible Python development environment on Windows.*

---

## About this guide

This repository is designed for **junior data analysts**, **data scientists**, and anyone starting to build Python projects professionally.

Rather than simply showing *which commands to run*, this guide explains **why** each tool exists and how they work together.

By the end of this guide, you will know how to:

- Install Python correctly
- Manage multiple Python versions with `pyenv`
- Create isolated virtual environments with `uv`
- Configure Visual Studio Code
- Organize Python projects
- Use Git and GitHub confidently
- Manage dependencies correctly
- Create reproducible projects that other people can run

The workflow presented here follows modern Python development practices and is suitable for both personal and professional projects.

---

# Tools used

| Tool | Purpose |
|-------|---------|
| Python | Programming language |
| Git | Version control |
| GitHub | Repository hosting and collaboration |
| pyenv-win | Manage multiple Python versions |
| uv | Manage virtual environments and dependencies |
| Visual Studio Code | Code editor |
| Ruff | Formatting, linting and import organization |
| Jupyter | Interactive notebooks |

---

## Learning path

The chapters are organised as an onboarding path, starting with the initial setup and gradually introducing the workflow used to create, maintain, and collaborate on Python projects.

Follow the chapters in order when setting up your environment for the first time. Each chapter can also be used independently as a reference when returning to a specific topic.

Throughout the guide, the examples use a fictional project named `sales-analysis`.

| Step | Chapter | Goal |
|---:|---|---|
| 00 | [Initial setup](00_Initial_Setup/00%20-%20Initial%20Setup.md) | Install and configure Git, pyenv-win, Python, uv, Visual Studio Code, and the extensions used throughout the guide |
| 01 | [Virtual environments and packages](01_Virtual_Environments_and_Packages/01%20-%20Virtual%20Environments%20and%20Packages.md) | Understand why projects use isolated environments and how pyenv, uv, `pyproject.toml`, and `uv.lock` work together |
| 02 | [Setting up Visual Studio Code](02_Set_Up_VS_Code/02%20-%20Setting%20up%20Visual%20Studio%20Code.md) | Configure VS Code, open projects correctly, and select the project’s Python interpreter |
| 03 | [Creating your first project](03_Create_A_First_Project/03%20-%20Creating%20Your%20First%20Project.md) | Create and organise a Python project for data analysis, install Jupyter, and prepare its `.gitignore` |
| 04 | [Managing dependencies with uv](04_Managing_Dependencies/04%20-%20Managing%20Dependencies%20with%20uv.md) | Add, remove, and synchronise project dependencies while understanding the role of the project configuration and lockfile |
| 05 | [Daily workflow](05_Daily_Workflow/05%20-%20Daily%20Workflow.md) | Follow a consistent routine for opening projects, synchronising environments, running code, and adding dependencies |
| 06 | [Version control with Git](06_Version_Control_with_Git/06%20-%20Version%20Control%20with%20Git.md) | Track changes, create meaningful commits, and synchronise work with a remote Git repository |
| 07 | [Growing a project](07_Growing_a_Project/07%20-%20Growing%20a%20Project.md) | Recognise when a project needs more structure and separate exploratory notebooks from reusable Python code |
| 08 | [Troubleshooting](08_Troubleshooting/08%20-%20Troubleshooting.md) | Diagnose and resolve common issues involving Python versions, dependencies, PowerShell, Git, and VS Code |

> [!NOTE]
> Chapters 00 to 03 provide the foundations needed to create a new project.  
> Chapters 04 to 08 can also be revisited independently as day-to-day references.

---

# Course Structure

The guide is divided into several chapters.

## Part 0 — Initial Setup

Install and configure the required tools.

- Git
- pyenv-win
- Python
- uv
- Visual Studio Code

**Start here**

---

## Part 1 — Virtual Environments & Packages

Understand:

- why virtual environments exist;
- why installing packages globally is discouraged;
- how `pyproject.toml` works;
- what `uv.lock` is;
- how Python dependencies are managed.

---

## Part 2 — Configure Visual Studio Code

Configure VS Code for Python development.

Learn:

- recommended extensions;
- useful settings;
- selecting the correct interpreter;
- integrating with Git.

---

## Part 3 — Create a New Python Project

Build your first professional Python project.

Topics include:

- Git initialization
- Selecting the Python version
- Creating a virtual environment
- Installing dependencies
- Opening the project in VS Code

---

## Part 4 — Create a Good `.gitignore`

Understand which files should (and should not) be committed to Git.

---

## Part 5 — Daily Workflow

A practical day-to-day workflow for Python development.

Examples include:

- starting work;
- installing packages;
- running code;
- synchronizing environments;
- committing changes.

---

## Part 6 — Git Tutorial

Learn the Git fundamentals needed for day-to-day development.

Topics include:

- commits;
- branches;
- merging;
- GitHub;
- collaboration.

---

## Part 7 — Troubleshooting

Common installation and configuration issues, including:

- `pyenv` not recognised;
- PowerShell execution policy;
- incorrect Python interpreter;
- missing packages;
- Git issues.

---

## Part 8 — Recommended Habits

A collection of good practices that make Python projects easier to maintain and collaborate on.

---

# Typical Project Structure

By following this guide, your projects will typically look like this:

```text
sales-analysis/

├── .git/
├── .venv/
├── .python-version
├── .gitignore
├── pyproject.toml
├── uv.lock
├── README.md
│
├── notebooks/
├── src/
├── tests/
└── data/
```

---

# Recommended Workflow

Every new project follows the same simple workflow.

```text
Create project
        ↓
git init
        ↓
pyenv local
        ↓
uv init
        ↓
uv add ...
        ↓
code .
        ↓
Start coding
```

Following the same workflow for every project makes your development environment predictable, reproducible, and easy to maintain.

---

# Who is this guide for?

This guide is intended for:

- Junior Data Analysts
- Junior Data Scientists
- Students learning Python
- Analysts transitioning from Excel to Python
- Professionals looking for a modern Python workflow

No previous knowledge of Git, virtual environments, or dependency management is assumed.

---

# Contributions

Suggestions, corrections, and improvements are always welcome.

If you find an error or have an idea to improve the guide, feel free to open an Issue or submit a Pull Request.

---

Happy coding! 
