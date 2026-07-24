## Part 2 — Configure VS Code

Open VS Code settings JSON:

Ctrl + Shift + P
Preferences: Open User Settings (JSON)

Use this configuration:

{
    "editor.formatOnSave": true,
    "editor.tabSize": 4,
    "editor.rulers": [88],
    "files.trimTrailingWhitespace": true,
    "files.insertFinalNewline": true,

    "python.defaultInterpreterPath": "${workspaceFolder}\\.venv\\Scripts\\python.exe",
    "python.terminal.activateEnvironment": true,
    "python.analysis.typeCheckingMode": "basic",

    "[python]": {
        "editor.defaultFormatter": "charliermarsh.ruff"
    },

    "editor.codeActionsOnSave": {
        "source.fixAll.ruff": "explicit",
        "source.organizeImports.ruff": "explicit"
    },

    "git.autofetch": true,
    "git.confirmSync": false,

    "terminal.integrated.defaultProfile.windows": "PowerShell"
}
