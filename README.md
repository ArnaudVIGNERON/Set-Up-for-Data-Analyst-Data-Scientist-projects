# Set-Up-for-Data-Analyst-Data-Scientist-projects

Python Development Setup Guide for Junior Data Analysts

This guide explains how to set up and use a modern Python development environment on Windows.

It is designed for junior data analysts who want a clean, professional, and reproducible workflow using:

Windows PowerShell
Git
GitHub
Visual Studio Code
pyenv-win
uv
virtual environments
Ruff
Jupyter notebooks

The goal is not only to install tools, but to understand how they work together.

Recommended Workflow

For every Python project, we want the same clean structure:

project-name
├── .git
├── .venv
├── .python-version
├── .gitignore
├── pyproject.toml
├── uv.lock
├── README.md
├── notebooks
├── data
├── src
└── tests

Each tool has a specific role:

Tool	Purpose
Git	Track code changes
GitHub	Store and share projects online
VS Code	Write and run code
pyenv-win	Manage Python versions
uv	Manage virtual environments and packages
Ruff	Format code and detect issues
Jupyter	Explore data interactively
