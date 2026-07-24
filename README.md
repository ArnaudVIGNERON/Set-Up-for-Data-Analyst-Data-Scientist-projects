# Python Onboarding Guide for Data Analysts & Data Scientists

A practical onboarding guide for setting up and working on modern Python projects.

This repository is designed for junior data analysts, data scientists, interns, and anyone who wants to adopt a professional Python workflow from the beginning.

Rather than teaching Python itself, this guide focuses on everything that surrounds a Python project:

- setting up a development environment
- managing Python versions
- creating reproducible projects
- working with virtual environments
- using Git and GitHub
- organising projects
- developing good day-to-day habits

The goal is simple:

> Build Python projects that are easy to understand, reproduce, and maintain.

---

# Who is this guide for?

This guide is intended for:

- Junior Data Analysts
- Junior Data Scientists
- Interns
- Students preparing for a first data role
- Anyone looking to adopt a modern Python workflow

Although the examples focus on data analysis, the workflow can be applied to most Python projects.

---

# Tools used throughout this guide

| Tool | Purpose |
|------|---------|
| Git | Version control and collaboration |
| pyenv-win | Manage multiple Python versions |
| Python | Programming language |
| uv | Virtual environments and dependency management |
| Visual Studio Code | Code editor |
| Jupyter | Exploratory analysis |

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

# Repository philosophy

Throughout this guide, we'll follow a few simple principles.

- Keep projects simple until they need to grow.
- One project, one virtual environment.
- Record dependencies instead of installing packages manually.
- Prefer reproducible workflows over manual configuration.
- Organise projects so they're easy to understand six months later.
- Write code that your future self—and your teammates—can easily work with.

---

# Repository structure

```text
00_Initial_Setup/
01_Virtual_Environments_and_Packages/
02_Setting_Up_Visual_Studio_Code/
03_Creating_Your_First_Project/
04_Managing_Dependencies_with_uv/
05_Daily_Workflow/
06_Version_Control_with_Git/
07_Growing_a_Project/
08_Troubleshooting/
```

Each chapter contains:

- explanations
- practical examples
- diagrams
- screenshots
- summaries
- cheat sheets

---

# Future improvements

This repository is intentionally focused on the foundations of professional Python development.

Future repositories will build on these concepts and introduce topics such as:

- Docker
- dbt
- Airflow
- Testing
- CI/CD
- Cloud platforms
- Production data workflows

---

# Feedback

This repository is continuously improved through real onboarding sessions.

If you find something unclear, discover a mistake, or have suggestions for improvement, feel free to open an issue or submit a pull request.

Every piece of feedback helps make the guide more useful for future readers.

Happy coding! 
