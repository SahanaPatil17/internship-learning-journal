# Chapter 05 – Git & GitHub Setup, SSH Authentication and Workflow

## Overview
This session focused on **Git and GitHub fundamentals**, including repository creation, SSH-based authentication, cloning repositories, committing changes, and troubleshooting common Git errors. The session emphasized why **Linux/WSL-based workflows** are preferred for the course and introduced GitHub Copilot usage.

---

## Key Topics Covered

### 1. Course Workflow & Assignments
- Assignments can be completed using provided instructions.
- Videos provide **context, best practices, and troubleshooting guidance**.
- LLMs can assist, but understanding workflows is important.

---

### 2. Why Git is Required
- Git is a **version control system** used to:
  - Track changes
  - Collaborate with others
  - Maintain history of code
- Git is mandatory for:
  - Submitting assignments
  - Managing projects
  - Collaboration in later modules

---

### 3. Git Installation
- Git must be installed separately for each environment:
  - Windows
  - WSL (Linux)
- Git installed on Windows does **not automatically work inside WSL**.
- Verification command:
  - `git --version`

---

### 4. GitHub Repositories
- A GitHub account is required.
- Repositories can be created:
  - Using GitHub web interface
  - Locally and pushed later
- A single GitHub account can host multiple repositories.

---

### 5. Local vs Remote Repositories
- **Local repository:** Exists on the user’s system
- **Remote repository:** Hosted on GitHub
- Git connects both using authentication mechanisms.

---

### 6. Authentication Methods
- Two main methods:
  - **HTTPS**
  - **SSH** (recommended)
- SSH avoids repeated password/token entry.
- SSH is preferred for long-term development workflows.

---

### 7. SSH Key Generation
- SSH uses a **key pair**:
  - Private key (kept on local machine)
  - Public key (uploaded to GitHub)
- Keys are stored in the `.ssh` directory.
- Public key is added under:
  - GitHub → Settings → SSH and GPG keys

---

### 8. SSH Agent
- SSH agent manages loaded keys.
- If keys are not loaded, cloning/pushing may fail.
- Keys may need to be reloaded after reboot in some cases.

---

### 9. Cloning a Repository
- Repositories can be cloned using SSH.
- Common error:
  - `Permission denied (publickey)`
- Usually caused by:
  - Missing SSH key
  - SSH agent not running
  - Wrong GitHub account linked

---

### 10. Git Workflow Basics
- Key commands:
  - `git status` – check repository state
  - `git add <file>` – stage files
  - `git commit -m "message"` – save changes
  - `git push` – upload changes to GitHub
- Commits represent checkpoints in project history.

---

### 11. Branches
- A repository can have multiple branches.
- `main` is the default branch.
- Branches allow:
  - Feature isolation
  - Experimentation
- Introduced conceptually (used extensively later).

---

### 12. Troubleshooting Git Errors
- Common issues:
  - Permission denied
  - Wrong credentials cached
  - SSH keys not loaded
- Windows Credential Manager may store old GitHub credentials.
- Reloading VS Code or terminal may resolve sync issues.

---

### 13. GitHub Copilot (Introduction)
- AI coding assistant integrated with VS Code.
- Available via GitHub Education Pack.
- Helps with:
  - Code generation
  - Documentation
  - Boilerplate creation
- Generated code must always be **reviewed and validated**.

---

## Summary
This session established the foundation for using Git and GitHub effectively, focusing on SSH authentication, repository workflows, and troubleshooting. These concepts are essential for all future assignments and project work.
