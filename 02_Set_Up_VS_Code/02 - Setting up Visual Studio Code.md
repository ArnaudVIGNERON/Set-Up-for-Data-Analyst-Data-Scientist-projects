---
title: 02 - Setting up Visual Studio Code
author: Arnaud Vigneron
date: 2026-07-24
tags:
  - visual studio code
  - python
  - tutorial
---

# 02 - Setting up Visual Studio Code

## Goal

In this chapter, we'll prepare Visual Studio Code for Python development and configure it to work with the workflow introduced in the previous chapter.

We'll also establish a few habits that we'll use throughout the rest of this guide, such as opening projects from a PowerShell terminal and working with the project's virtual environment.

## Prerequisites

Before starting this chapter, you should have completed:

- 00 - Initial Setup
- 01 - Virtual Environments and Packages

or already have:

- Visual Studio Code installed
- The recommended extensions installed
- A Python project created with `uv`

## Learning objectives

After completing this chapter, you'll be able to:

- open a project correctly in Visual Studio Code
- understand how VS Code detects the project environment
- select the correct Python interpreter
- configure Visual Studio Code for the workflow used throughout this guide
- verify that everything is working before writing code

---

## Why this matters

Visual Studio Code is where we'll write, run, and debug our Python code.

Rather than opening individual Python files, we'll always open the project itself.

Opening the project allows Visual Studio Code to automatically detect the project's Git repository, virtual environment, Python interpreter, and configuration files.

Once the project is open, all of the tools introduced in the previous chapters work together automatically.

---

## Opening a project

Throughout this guide, we'll open our projects from a PowerShell terminal.

First, navigate to the project folder.

```powershell
cd .\Python_Projects\sales-analysis\
```

Then open the project with:

```powershell
code .
```

The `.` represents the current directory.

Rather than opening a single file, `code .` tells Visual Studio Code to open the entire project.

This allows VS Code to automatically detect:

- the Git repository
- the virtual environment
- the Python interpreter
- the project configuration files

Throughout the rest of this guide, we'll assume projects are opened using `code .`.

The following screenshot shows the typical workflow.

<img src="img/Open_VS_Code_Project.png" width="900">

Once the project opens, the Explorer displays the complete project structure, including the virtual environment and the configuration files introduced in the previous chapter.

We'll use this view throughout the rest of the guide.
