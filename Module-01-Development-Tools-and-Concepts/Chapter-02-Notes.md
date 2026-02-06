# Chapter/Session 02 – Development Environment & Version Control Basics

## Overview
This chapter focused on setting up the foundational development environment required for the **Tools in Data Science (TDS)** course. The session introduced Linux-based workflows, Windows Subsystem for Linux (WSL), Ubuntu, and the fundamentals of Git and GitHub.

---

## Key Concepts Covered

### 1. Terminals & Command Line Interfaces
- A **terminal** allows interaction with the operating system using commands.
- Different operating systems use different shells:
  - Windows: PowerShell
  - Linux / macOS: Bash / Zsh
- Command-line tools are essential for automation, development, and data workflows.

---

### 2. Windows Subsystem for Linux (WSL)
- WSL enables running a **Linux environment directly on Windows** without a traditional virtual machine.
- Advantages:
  - Faster than VirtualBox
  - Direct integration with Windows files
  - Industry-standard Linux tooling
- WSL uses **Hyper-V (Type 1 Hypervisor)** internally.

---

### 3. WSL vs VirtualBox
| Feature | WSL | VirtualBox |
|------|-----|------------|
| Performance | Fast | Slower |
| Resource usage | Lightweight | Heavy |
| GUI | Limited | Full GUI |
| Industry usage | High | Moderate |

---

### 4. Ubuntu on WSL
- Ubuntu is a popular Linux distribution.
- Ubuntu LTS (Long Term Support) versions are stable and recommended.
- Ubuntu provides access to Linux package managers and development tools.

---

### 5. Git – Version Control System
- Git tracks changes in files over time.
- Key Git concepts:
  - Repository
  - Commit
  - History
  - Rollback
- Git allows recovery of previous versions of code.

---

### 6. GitHub – Remote Code Hosting
- GitHub is a cloud platform for hosting Git repositories.
- Benefits:
  - Code backup
  - Collaboration
  - Deployment support
- GitHub Actions enable automation and CI/CD pipelines.

---

## Summary
This chapter laid the groundwork for future modules by introducing Linux environments and version control, both of which are essential tools in modern data science and software development workflows.
