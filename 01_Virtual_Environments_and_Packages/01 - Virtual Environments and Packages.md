---
title: 01 - Virtual Environments and Packages
author: Arnaud Vigneron
date: 2026-07-24
tags:
  - python
  - tutorial
---

# 01 - Installing Python Packages

Using Python for exploring and processing data is all about learning how to use the relevant open source packages like `pandas` or `numpy`, which have been created by the open source community over the span of more than 30 years. These additional packages are called *dependencies* because your project imports and uses them.

In this document, we will describe a best practice on how to manage dependency installations that is
- Convenient
- Reliable
- Reproducible

...using a Python virtual environment + dependency manager.

If you are already familiar with virtual environments and know how to use tools like `uv`, `pdm` or `conda`. You can skip this document.


## 2.1 - Not recommended way of installing Python packages

In Python tutorials or in Python courses you frequently encounter that dependencies are installed directly with a command line tool called `pip`:

```shell
pip install pandas  # Installs the pandas package to your local System Python installation
pip install numpy   # Installs the numpy package to your local System Python intallation
```

However, this would lead to a scenario where all your packages are being installed to your local System Python installation. This becomes not feasible quickly once you work on multiple projects, because different projects are very likely to require different packages and even different versions of the same package. Re-installing the correct version of a package every time you work on a new project becomes un-manageable.

*Not recommended:*

<img src="img/local_setup.jpg" width="450">

## 2.2 - Explaining Python virtual environments

When using a virtual environment management tool, it essentially means that you only need to install this single tool `uv` to your local System Python installation.

This tool will then be used to create a virtual environment for each Python project that you are working on. All package depencies are then installed via `uv` into the virtual environment and not on your local System Python installation.

An example is given below:

*Use a virtual environment for a project and install package dependencies only inside the virtual environment.*

<img src="img/venv_setup.jpg" width="450">

In the following, we will explain the details of the above figure. For now only reading through the explanation is enough. A separate hands-on tutorial will follow later.

Your and other people's Python projects are hosted in repositories on Github. You download a local copy of the repository using the version control tool `git`. You can modify the code and save changes to the repository as well.

Each Python repository contains a file called `pyproject.toml`. This file contains all the information of your Python project that are needed for you and anyone else to install your project as its own Python package and to run your code.

An example `pyproject.toml` is given below:
```text
# pyproject.toml

[build-system]   # Needed to install your project as its own Python package that can be imported by other projects
requires = ["setuptools", "wheel"]
build-backend = "setuptools.build_meta"


[project]        # Main Project specifications
# AV 621 project metadata
# See https://www.python.org/dev/arnauds/av-0621/
name = "python-onboarding"
version = "0.0.1"
description = "A short description of the project"
authors = [
    {name = "Arnaud Vignrton", email = "arnaud.vigneron@xxxx.com"},
]
requires-python = ">=3.10,<3.13"

dependencies = [  # Dependencies that are needed to run your program as a user
    'numpy',
    'pandas',
    "matplotlib"
]


[project.optional-dependencies]  # Optional dependencies with tools that help during development
testing = [        # A dependency group called testing
    'pytest'       # Unit / Integration tests
]

linting = [        # A dependency group called linting
    'ruff'         # Linting
]

dev = [  # A dependency group that contains all other groups
    'python-onboarding[testing,linting]'  # Include all previous specified groups
]

```

The name of your Python project/package name is specified under the section `[project]`:
```text
[project]        # Main Project specifications
# AV 621 project metadata
# See https://www.python.org/dev/arnauds/av-0621/
name = "python-onboarding"
version = "0.0.1"
```

The Python version is there as well:
```text
[project]        # Main Project specifications
...
requires-python = ">=3.10,<3.13"
```

All Python dependencies that need to be installed additionally are specified as a list under `dependencies`

```text
[project]        # Main Project specifications
...
dependencies = [  # Dependencies that are needed to run your program as a user
    'numpy',
    'pandas',
    "matplotlib"
]
```

and `[project.optional-dependencies]`:

```text
[project.optional-dependencies]  # Optional dependencies with tools that help during development
testing = [        # A dependency group called testing
    'pytest'       # Unit / Integration tests
]

linting = [        # A dependency group called linting
    'ruff'         # Linting
]

dev = [  # A dependency group that contains all other groups
    'eec-python-onboarding[testing,linting]'  # Include all previous specified groups
]

```

Using the tool `uv`, the command `pdm init` will then automatically create a virtual environment and install your Python project as well all specified dependencies into it.

Note: When you create a new Python project from a template, you usually don't need to worry about setting up the optional dependencies yourself. But you are free to customize and choose different tools that makes developing code easier for you.

Using the `pyproject.toml` file to specify all dependencies in combination with a virtual environment allows it for anyone collaborating in your Python project to reproduce the exact same development environment.

*Anyone can reproduce the exact same environment.*

<img src="img/collab_setup.jpg" width="900">

Note that which tools you prefer to use is up to you, as long as it is compliant with the `pyproject.toml` format. As an example in the figure above, Computer 2 could use a different virtual environment management tool called `conda` to create the virtual environment and install the dependencies.


You can also easily create and work with several Python projects in parallel yourself:

<img src="img/multiple_project_setup.jpg" width="900">

Each project is developed in isolation within its own virtual environment. And your team members can easily reproduce your results and help you writing code by having the exact same virtual environment.

If a project requires a different Python version, you can use `pyenv` to easily switch to the correct Python version before running `uv init`.
