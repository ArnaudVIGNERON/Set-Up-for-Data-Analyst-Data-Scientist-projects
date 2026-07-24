# Part 4 — Create a Good .gitignore

The `.gitignore` file tells Git what not to track.

Create it:

```powershell
New-Item .gitignore
```

Recommended content:

```gitignore
# Virtual environment
.venv/

# Python cache
__pycache__/
*.py[cod]
*$py.class

# Environment variables and secrets
.env
.env.*

# Jupyter
.ipynb_checkpoints/

# Data files
data/raw/
data/private/

# Logs
*.log

# VS Code
.vscode/*
!.vscode/settings.json
!.vscode/extensions.json

# OS files
.DS_Store
Thumbs.db
```

Important:

* Commit `.python-version`
* Commit `pyproject.toml`
* Commit `uv.lock`
* Do not commit `.venv`
* Do not commit `.env`
* Do not commit private or raw sensitive data
