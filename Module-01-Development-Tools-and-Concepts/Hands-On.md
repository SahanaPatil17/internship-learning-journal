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


