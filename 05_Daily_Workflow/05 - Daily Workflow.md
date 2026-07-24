# Part 5 — Daily Workflow

## Start work

```powershell
cd path\to\project
.venv\Scripts\Activate.ps1
code .
```

Check Python:

```powershell
python --version
```

Check Git status:

```powershell
git status
```

---

## Add a package

```powershell
uv add pandas
```

This updates:

```text
pyproject.toml
uv.lock
```

Both files should be committed.

---

## Run code

```powershell
uv run python src/main.py
```

Or, if your environment is activated:

```powershell
python src/main.py
```

---

## Sync an existing project

When cloning a project that already has `pyproject.toml` and `uv.lock`:

```powershell
git clone <repository-url>
cd project-name
pyenv install
uv sync
code .
```
