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

Happy coding! 🚀
