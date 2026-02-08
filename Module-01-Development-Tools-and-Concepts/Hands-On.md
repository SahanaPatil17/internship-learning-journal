# Week 1 – Session 1  
## Practical Setup and Environment Preparation

### Platform Familiarization
- Identified the correct portals for:
  - Learning and announcements (Course Portal)
  - Graded submissions (Seek Portal)

### Environment Setup
- Introduction to **Windows Subsystem for Linux (WSL)**.
- Understood the importance of Linux environments for data science tasks.

### WSL Installation Overview
- Enabled WSL on a Windows system.
- Installed a Linux distribution.
- Verified installation using terminal commands.
- Prepared the local system for upcoming hands-on exercises.

### Practical Exposure
- Navigated basic command-line interfaces.
- Understood initial environment setup workflows.

> **Note:** Understood how to do everything but couldn't install Ubuntu because of internal system issues.

# Week 1 Session 2

## Objective
To set up a Linux-based development environment and understand the basics of Git-based version control.

---

## Tasks Attempted

### 1. WSL Installation (Windows)
- Followed the official steps to install WSL using PowerShell.
- Enabled required Windows features:
  - Windows Subsystem for Linux
  - Virtual Machine Platform
  - Hypervisor Platform
- Restarted the system multiple times as instructed.

⚠️ **Outcome:**  
Despite multiple attempts, WSL/Ubuntu could not be successfully installed due to system-level issues. The setup process was retried using different methods (PowerShell, Microsoft Store), but the Ubuntu environment could not be stabilized.

---

### 2. Ubuntu Setup
- Attempted installation of Ubuntu (LTS version) via WSL.
- Faced repeated access/initialization errors during setup.
- Due to these issues, Ubuntu could not be fully configured on the system.

---

### 3. Git (Conceptual Hands-On)
- Understood Git workflow through live demonstration:
  - `git init`
  - `git add`
  - `git commit`
- Observed how Git tracks file changes and enables rollback.
- Learned how Git integrates with GitHub for remote hosting.

---

## Current Status
- WSL/Ubuntu setup: ❌ Not completed (system issue)
- Git concepts: ✅ Understood
- GitHub workflow: ✅ Understood conceptually

---

## Note
Further hands-on practice with Git and Linux commands will be performed once the Linux environment is successfully configured or via an alternative system if required.

# Week 1 Session 3

## Objective
To understand Linux file system navigation, command-line concepts, and set up terminal-based AI tools (`uv` and `llm`).

---

## Tasks Attempted

### 1. WSL & Ubuntu Usage
- Followed the session walkthrough explaining:
  - Linux root directory
  - Home directory structure
  - Mounted Windows drives under `/mnt`
- Understood how Linux files and Windows files coexist in WSL.

⚠️ **Outcome:**  
WSL/Ubuntu could not be successfully installed or stabilized on my system despite repeated attempts in earlier sessions. Due to this, hands-on execution of Linux commands could not be performed locally.

---

### 2. Linux Command Concepts (Conceptual)
- Learned the purpose and usage of:
  - `ls` (list files)
  - `cd` (change directory)
  - Absolute vs relative paths
  - `.` and `..` directory references
- Understood Linux directory hierarchy and navigation logic.

---

### 3. VS Code Terminal (Conceptual)
- Observed how VS Code integrates:
  - File Explorer
  - Terminal
  - WSL environment
- Understood how terminal location maps to actual file paths.

---

### 4. UV Tool Installation
- Observed installation process for `uv`:
  - Installed via Linux/Mac terminal
  - Placed in system `bin` directory
- Learned how to verify installation using:
  - `uv --version`

---

### 5. LLM Tool Setup
- Learned how to install `llm` using:
  - `uv tool install llm`
- Understood that `llm` enables terminal interaction with AI models.

---

### 6. API Key Configuration (Conceptual)
- Gemini API:
  - Generated using Google AI Studio
  - Configured via `llm key set gemini`
- OpenAI / AI-Pipe:
  - Token generated via IITM AI-Pipe portal
  - Base URL added to shell configuration file (`.bashrc` / `.zshrc`)
- Learned importance of environment variables and shell restart.

---

## Current Status
- WSL / Ubuntu: ❌ Not working on system
- Linux navigation concepts: ✅ Understood
- UV & LLM workflow: ✅ Understood conceptually
- API usage flow: ✅ Understood

---

## Note
Hands-on execution will be completed once a working Linux environment is available, either via system fix or alternative setup.

# Week 1 - Session 4

## Objective
To understand and set up a modern development environment using VS Code, package managers, Python versioning, GitHub CLI, and command-line AI tools.

---

## Tasks Attempted

### 1. VS Code & GitHub Setup (Conceptual)
- Understood correct VS Code installation practices on macOS.
- Learned how to link VS Code with GitHub account.
- Understood activation and usage of GitHub Copilot via Education Pack.

---

### 2. Package Manager Usage (Conceptual)
- Learned the purpose and advantages of Homebrew.
- Understood dependency management and PATH configuration.
- Compared macOS/Linux package managers with Windows workflows.

---

### 3. Python Version Management (Conceptual)
- Learned why Python version pinning is important.
- Understood usage of pyenv for:
  - Global Python version
  - Project-specific Python version
- Observed how system Python differs from managed Python versions.

---

### 4. UV Project Initialization (Conceptual)
- Observed how `uv init`:
  - Creates project structure
  - Initializes Git repository
  - Manages virtual environments automatically
- Learned how dependencies are added and removed using UV.

---

### 5. GitHub CLI Workflow (Conceptual)
- Learned how to:
  - Authenticate GitHub via terminal
  - Create repositories using CLI
  - Push local repositories without using the web interface
- Understood importance of CLI workflows for automation.

---

### 6. LLM CLI Setup & Usage (Conceptual)
- Learned installation of `llm` CLI tool.
- Understood API key configuration for:
  - OpenAI (via AI Pipe)
  - Gemini (via plugin)
- Observed usage of different models using CLI flags.

---

### 7. AI Automation Demo (Observed)
- Observed audio transcription using LLM CLI.
- Learned how multimodal inputs (audio/text) are handled.
- Understood cost-efficient model selection strategies.

---

## Current Status
- WSL / Linux environment: ❌ Not functional on system
- macOS/Linux setup: ❌ Not applicable
- Conceptual understanding of workflows: ✅ Strong

---

## Note
Hands-on execution will be completed once a functional Linux environment (WSL or alternative) is available.

# Week 1 Session 5

## Objective
To set up Git and GitHub connectivity using SSH and understand the complete Git workflow from local development to remote repositories.

---

## Tasks Attempted

### 1. Git & GitHub Setup (Conceptual)
- Understood Git installation requirements for Windows and WSL separately.
- Learned how to verify Git installation using `git --version`.

---

### 2. Repository Creation (Observed)
- Observed repository creation via GitHub web interface.
- Understood repository structure under a GitHub username.
- Learned that repositories can be created locally and pushed later.

---

### 3. SSH Authentication Setup (Observed)
- Learned how to generate SSH key pairs.
- Understood difference between public and private keys.
- Observed how to add public SSH key to GitHub settings.

---

### 4. Cloning with SSH (Observed)
- Observed cloning a GitHub repository using SSH.
- Understood common SSH-related errors and their causes.
- Learned importance of SSH agent for key management.

---

### 5. Git Workflow (Observed)
- Observed adding files using `git add`.
- Observed committing changes with descriptive commit messages.
- Observed pushing changes to GitHub using `git push`.

---

### 6. Troubleshooting Git Issues (Observed)
- Learned how cached credentials can cause permission errors.
- Observed use of Windows Credential Manager for fixing conflicts.
- Learned that VS Code reload may be required after authentication changes.

---

### 7. GitHub Copilot Demo (Observed)
- Observed Copilot generating markdown and code files.
- Learned how AI-generated content can be pushed to GitHub.
- Understood importance of validating AI output before committing.

---

## Current Status
- WSL / Linux environment: ❌ Not stable on system
- SSH-based GitHub workflow: ✅ Understood conceptually
- Git commands and flow: ✅ Understood
- Copilot usage: ✅ Understood conceptually

---

## Note
Hands-on execution will be completed once a stable Linux/WSL environment is available or via an alternative setup.


