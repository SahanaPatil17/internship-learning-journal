# Chapter/Session 04 – Development Environment Setup (macOS & Linux)

## Overview
This session provided a comprehensive walkthrough for setting up a modern development environment on **macOS and Linux systems**. The focus was on editor setup, package management, Python version control, project automation, GitHub workflows, and command-line AI tooling.

Although the session was demonstrated on macOS/Linux, the workflows are intended to be replicated on **Windows via WSL**, which is functionally equivalent to Linux.

---

## Key Topics Covered

### 1. Development Environment Philosophy
- Course workflows assume a **Linux-based environment**.
- macOS is Unix-based and closely aligned with Linux under the hood.
- Windows users are expected to use **WSL** to match Linux behavior.

---

### 2. Visual Studio Code (VS Code)
- Recommended primary code editor for the course.
- On macOS:
  - VS Code must be moved to the **Applications** folder after download.
  - Running from Downloads may cause permission and update issues.
- VS Code integrates:
  - File explorer
  - Terminal
  - Git & GitHub
  - AI tools (Copilot)

---

### 3. GitHub Education Pack & Copilot
- GitHub Education Pack provides:
  - GitHub Copilot Pro
  - Monthly AI credits
- Copilot must be:
  - Activated on GitHub website
  - Linked to VS Code using the same GitHub account
- Provides access to premium AI models directly inside VS Code.

---

### 4. Package Managers
- **Homebrew** (macOS/Linux):
  - Command-line package manager
  - Simplifies installation and updates
  - Automatically handles dependencies
- Linux equivalents:
  - `apt`, `yum`, `pacman`
- Package managers ensure stability and reproducibility.

---

### 5. PATH Environment Variable
- PATH determines where the system looks for executables.
- Adding tools to PATH allows them to run from any directory.
- After installing Homebrew or UV, PATH configuration is required.

---

### 6. Python Version Management (pyenv)
- pyenv allows:
  - Multiple Python versions on the same system
  - Project-specific Python versions
- Reasons for version control:
  - Latest Python versions may break dependencies
  - Stable versions are preferred for deployment
- Supports:
  - System Python
  - Global Python version
  - Local (project-specific) Python version

---

### 7. UV – Modern Python Project Manager
- UV replaces traditional workflows involving:
  - `pip`
  - `virtualenv`
- Features:
  - Creates virtual environments automatically
  - Manages dependencies efficiently
  - Uses a shared package cache (memory-efficient)
- `uv init`:
  - Creates project structure
  - Initializes Git repository
  - Adds `.gitignore`, README, dependency files

---

### 8. GitHub CLI (gh)
- Enables GitHub operations directly from the terminal.
- Supports:
  - Authentication
  - Repository creation
  - Pushing code without web UI
- Essential for automation and CI/CD workflows.

---

### 9. Git Basics via Terminal
- Key commands discussed:
  - `git add`
  - `git commit`
  - Repository initialization
- `.gitignore` prevents sensitive or large files from being tracked.
- Emphasis on automation rather than GUI-only workflows.

---

### 10. LLM Command-Line Tool
- `llm` enables interaction with AI models from the terminal.
- Supports:
  - OpenAI models (via AI Pipe)
  - Gemini models (via plugin)
- Requires:
  - API key configuration
  - Optional base URL configuration
- CLI-based AI enables:
  - Automation
  - Intelligent agents
  - Non-interactive workflows

---

### 11. Model Sel
