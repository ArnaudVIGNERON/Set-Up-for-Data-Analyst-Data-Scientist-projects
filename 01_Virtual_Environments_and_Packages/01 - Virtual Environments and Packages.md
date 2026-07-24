---
title: 01 - Virtual Environments and Packages
author: Arnaud Vigneron
date: 2026-07-24
tags:
  - python
  - tutorial
  - uv
---

# 01 - Virtual Environments and Packages

## Goal

In this chapter, we'll look at how Python projects are organised.

We'll see why every project has its own Python environment, how packages are managed, and how the different files in a project work together.

The goal isn't to memorise every command or every project file. Instead, we'll focus on understanding the workflow we'll use throughout the rest of this guide.

## Prerequisites

Before starting this chapter, you should have completed:

- 00 - Initial Setup

or already have:

- Git installed
- pyenv-win installed
- Python installed
- uv installed

## Learning objectives

After completing this chapter, you'll be able to:

- explain why installing project packages globally becomes difficult as you work on more projects
- describe the purpose of a virtual environment
- understand the role of `pyproject.toml`
- understand the role of `uv.lock`
- explain how `pyenv` and `uv` work together

---

## Why this matters

One of the strengths of Python is the large number of packages available to the community. Whether you're cleaning data with `pandas`, creating visualisations with `matplotlib`, or building machine learning models with `scikit-learn`, most projects rely on packages developed and maintained by the open-source community.

As we work on more projects, we'll quickly notice that they don't all use the same packages or even the same versions of those packages. Some projects may also require a different version of Python.

Throughout this guide, we'll organise each project so that it remains independent from the others. This makes projects easier to maintain, easier to reproduce, and much easier to share with other developers.

We'll build this workflow progressively throughout the chapter.

---

## A common beginner approach

When learning Python, it's common to install packages directly with `pip`.

For example:

```powershell
pip install pandas
pip install numpy
```

There's nothing wrong with this approach when you're learning or experimenting with a single project.

The packages are installed into your default Python installation, and everything works as expected.

The situation changes as you begin working on multiple projects.

One project may require a newer version of `pandas`, while another still depends on an older version. Installing or upgrading a package for one project can unintentionally affect another.

The following diagram illustrates this situation.

Every project shares the same Python installation and the same collection of installed packages.

<img src="img/local_setup.jpg" width="450">

At first, this may seem convenient because everything is installed in one place.

As the number of projects grows, however, managing package versions becomes increasingly difficult. It also becomes harder to answer a simple question:

> Which packages are required to run this project?

Rather than sharing one Python installation between every project, we'll give each project its own isolated environment.


---

## One project, one environment

Instead of sharing one Python installation between every project, we'll create a dedicated environment for each project.

A virtual environment is simply an isolated Python installation that belongs to a single project.

It contains:

- the Python interpreter used by the project
- the packages installed for that project
- the command-line tools used during development

This means that installing or updating a package in one project has no impact on any other project.

The following diagram illustrates this approach.

<img src="img/venv_setup.jpg" width="450">

Each project has its own virtual environment and its own collection of installed packages.

As a result:

- projects remain independent from one another
- different package versions can coexist on the same computer
- each project can evolve without affecting the others

Throughout this guide, we'll use one virtual environment for every project we create.

---

## Managing environments with `uv`

Creating and maintaining virtual environments manually quickly becomes repetitive.

Throughout this guide, we'll use `uv` to manage our Python projects.

`uv` helps us:

- create new Python projects
- create virtual environments
- install and update packages
- keep track of project dependencies
- recreate the same environment on another computer
- run commands inside the correct environment

We'll use these features throughout the guide, so there's no need to memorise them now.

For the moment, it's enough to know that `uv` is the tool responsible for managing the project's environment.

---

## The project files

When we create a new Python project, a few files appear alongside our source code.

A typical project looks similar to this:

```text
sales-analysis/
├── .venv/
├── pyproject.toml
├── uv.lock
├── README.md
└── src/
```

Each of these files has a specific role.

We'll look at them one at a time.

---

## `pyproject.toml`

Every project contains a file called `pyproject.toml`.

You can think of it as the project's configuration file.

Among other things, it describes:

- the project's name
- the supported Python version
- the packages required by the project

A simplified example is shown below.

```toml
[project]
name = "sales-analysis"
version = "0.1.0"

requires-python = ">=3.12,<3.14"

dependencies = [
    "pandas",
    "numpy",
    "matplotlib",
]
```

We don't need to understand every line of this file yet.

For now, it's enough to know that `uv` reads this file to understand how the project should be configured.

As we create and maintain projects later in the guide, we'll come back to this file several times.

---

## Working with multiple projects

As we work on more projects, it's common for each of them to have different requirements.

For example:

- one project may use Python 3.11 while another uses Python 3.13
- one project may rely on an older version of `pandas`
- another project may require additional packages that are not needed elsewhere

Because each project has its own virtual environment, they can all coexist on the same computer without interfering with one another.

The following diagram illustrates this idea.

<img src="img/multiple_project_setup.jpg" width="900">

Each project remains independent and can evolve at its own pace without affecting the others.

---

## Selecting the Python version

So far, we've focused on the project's packages.

The Python version itself is just as important.

Throughout this guide, we'll use `pyenv` to manage the Python versions installed on our computer.

When we create a project, `pyenv` records the selected Python version in a file called `.python-version`.

For example:

```text
3.13.7
```

Whenever we open the project, `pyenv` automatically selects the correct Python version for us.

This means we don't have to remember which version of Python each project uses. The project itself keeps track of that information.

---

## Reproducing the same environment

Keeping projects independent is only part of the story.

We also want another developer to be able to recreate the same environment on their own computer.

That's where `uv.lock` comes in.

When packages are installed or updated, `uv` records the exact versions used by the project in the `uv.lock` file.

Instead of saying:

> Install a recent version of `pandas`

the project can say:

> Install exactly the versions that were used when this project was last updated.

This makes projects much more reproducible.

Whether the project is opened next week or next year, everyone starts from the same environment.

---

## Working as a team

Sharing a Python project doesn't mean sharing the virtual environment.

Each developer creates their own local environment.

The project files describe what that environment should contain.

The following diagram illustrates this workflow.

<img src="img/collab_setup.jpg" width="900">

When someone clones the repository, `uv` reads the project files and recreates the required environment on their computer.

Although each developer has their own virtual environment, everyone works with the same Python version and the same package versions defined by the project.

This makes collaboration much more predictable and greatly reduces "it works on my machine" problems.

---

## Bringing everything together

Let's take a step back and look at how these different tools work together.

When we create a new project, each tool has a specific responsibility.

- `Git` tracks the history of the project and makes collaboration possible.
- `pyenv` manages the Python version used by the project.
- `uv` creates the virtual environment and manages the project's packages.
- `Visual Studio Code` provides the development environment where we'll write, run, and debug our code.

The project itself keeps track of its configuration through a few files:

| File | Purpose |
|------|---------|
| `.python-version` | Specifies which version of Python the project uses |
| `pyproject.toml` | Describes the project and its packages |
| `uv.lock` | Records the exact package versions used by the project |

Together, these files make it possible to recreate the same development environment on another computer.

Whether you're returning to a project several months later or collaborating with another developer, the workflow remains the same.

---

## Summary

In this chapter, we've introduced the workflow we'll use throughout the rest of this guide.

Rather than sharing one Python installation between every project, we'll create an isolated environment for each one.

We'll use:

- `pyenv` to manage Python versions
- `uv` to create and manage project environments
- `pyproject.toml` to describe the project
- `uv.lock` to record the exact package versions used by the project

Together, these tools help us build projects that are easier to maintain, easier to reproduce, and easier to share.

---

## After completing this chapter

You should now be able to:

- explain why each project has its own virtual environment
- describe the role of `pyenv` within a project
- describe the role of `uv`
- explain the purpose of `pyproject.toml`
- explain the purpose of `uv.lock`
- understand how another developer can recreate the same project environment
