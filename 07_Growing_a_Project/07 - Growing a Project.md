---
title: 07 - Growing a Project
author: Arnaud Vigneron
date: 2026-07-24
tags:
  - python
  - project
  - structure
---

# 07 - Growing a Project

## Goal

In this chapter, we'll look at how a Python project naturally evolves over time.

We'll discuss when to introduce additional folders, how to organize code, and how to keep a project easy to navigate as it grows.

## Prerequisites

Before starting this chapter, you should already be comfortable creating and working on Python projects.

If not, Chapters 03 to 06 cover the workflow used throughout this guide.

## Learning objectives

After completing this chapter, you'll be able to:

- recognize when a project should be reorganized
- separate exploratory work from reusable code
- organize notebooks and Python files consistently
- keep projects easy to maintain as they grow

---

## Why this matters

Most projects start small.

As new analyses are added, more notebooks are created, and reusable code begins to emerge, the project structure naturally evolves.

Rather than trying to build the perfect structure from the beginning, it's often better to keep projects simple and reorganize them when the need becomes clear.

---

## Starting simple

Throughout this guide, we've used a simple project structure.

```text
sales-analysis/
├── notebooks/
├── .venv/
├── .gitignore
├── main.py
├── pyproject.toml
├── README.md
└── uv.lock
```

For many projects, this structure is perfectly sufficient.

It keeps notebooks, Python code, and project configuration together while remaining easy to understand.

There's no need to introduce additional folders until they provide a clear benefit.

---

## Recognizing when a project is growing

As a project evolves, you may notice that:

- notebooks become difficult to navigate
- code is copied between notebooks
- helper functions are reused in multiple places
- several people start contributing to the project

These are often good indicators that it's time to reorganize part of the project.

Growing a project isn't about making it more complex.

It's about making it easier to understand and maintain.

---

## Separating exploration from reusable code

Notebooks are excellent for exploration and experimentation.

As analyses mature, it's common to move reusable functions into Python files.

For example, a project might evolve from:

```text
sales-analysis/
├── notebooks/
│   ├── 01_exploration.ipynb
│   └── 02_visualizations.ipynb
├── main.py
```

to:

```text
sales-analysis/
├── notebooks/
│   ├── 01_exploration.ipynb
│   └── 02_visualizations.ipynb
│
├── data_processing.py
├── visualizations.py
└── main.py
```

This allows notebooks to focus on the analysis while reusable code lives in dedicated Python files.

Over time, if the project continues to grow, you may decide to introduce folders such as `src` or `tests`.

For many data analysis projects, however, this isn't necessary.

---

## Documentation

As projects grow, documentation becomes increasingly important.

A good `README.md` should help someone understand:

- what the project does
- how to install the dependencies
- how to run the project
- where important files are located

Good documentation helps both your future self and anyone else working on the project.

---

## Summary

Projects rarely keep exactly the same structure from beginning to end.

As they grow, introducing additional organization helps keep them easy to navigate and maintain.

The goal isn't to create the most sophisticated project structure possible.

The goal is to make the project easy to understand for yourself and for the people working with you.

---

## After completing this chapter

You should now be able to:

- recognize when a project should evolve
- separate notebooks from reusable code
- organize projects as they become larger
- keep project structures simple and maintainable

---

## Cheat Sheet

| Task | Recommendation |
|------|----------------|
| Explore a new dataset | Create a notebook |
| Reuse code | Move it into a Python file |
| Organize notebooks | Keep them in the `notebooks` folder |
| Document the project | Update the `README.md` |
| Add new folders | Only when they improve the project structure |
