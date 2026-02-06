# Chapter/Session 03 – Linux File System, CLI Basics & LLM Tooling

## Overview
This session focused on understanding how computers boot, how Linux environments work under WSL, and how to navigate the Linux file system using the command line. The session also introduced terminal-based AI tooling using `uv` and `llm` to interact with Gemini and GPT models.

---

## Key Concepts Covered

### 1. Computer Boot Process
- System startup flow:
  - Power on → BIOS / UEFI
  - Disk detection (SSD / HDD)
  - EFI partition identifies installed operating systems
  - Bootloader loads the selected OS
- Windows typically loads by default unless dual-boot is configured.

---

### 2. Hypervisors
- A **hypervisor** is software that allows multiple operating systems to share the same hardware.
- Types:
  - **Type 1 (Bare-metal):** Direct hardware access (used by WSL & cloud platforms)
  - **Type 2:** Runs on top of an OS (e.g., VirtualBox)
- WSL uses **Hyper-V**, making it faster than traditional virtual machines.

---

### 3. Linux File System Structure
- Linux follows a **single-root hierarchy**:
  - `/` → root directory
- Important directories:
  - `/home` → user directories
  - `/mnt` → mounted drives (e.g., Windows C:, D:)
  - `/bin` → installed binaries and commands
- The `~` (tilde) symbol represents the current user's home directory.

---

### 4. Absolute vs Relative Paths
- **Absolute paths** start from `/`
  - Example: `/home/user/test`
- **Relative paths** depend on the current directory
  - Example: `test/`
- Special symbols:
  - `.` → current directory
  - `..` → parent directory

---

### 5. Linux vs Windows File Systems
| Linux | Windows |
|-----|--------|
| Single root (`/`) | Multiple drives (C:, D:) |
| Forward slash `/` | Backslash `\` |
| Everything is mounted | Drives accessed separately |

- Windows drives appear in Linux under `/mnt`.

---

### 6. Command-Line Basics
- `ls` – list directory contents
- `cd` – change directory
- `clear` – clear terminal screen
- CLI tools are essential for automation and scripting.

---

### 7. VS Code Terminal Integration
- VS Code can open multiple terminals:
  - PowerShell
  - WSL
  - Bash
- When WSL is enabled, VS Code can directly open folders in the Linux environment.

---

### 8. UV Tool
- `uv` is a fast Python-based tool manager.
- Used for:
  - Installing CLI tools
  - Managing Python utilities
  - Creating virtual environments
- Installed globally and placed in `/bin`.

---

### 9. LLM Tool
- `llm` is a command-line interface to interact with:
  - Gemini models
  - OpenAI GPT models
- Supports:
  - Model selection
  - API key configuration
  - Terminal-based AI queries

---

## Summary
This session emphasized Linux fundamentals, command-line navigation, and introduced terminal-based AI tooling, which will be heavily used for automation and experimentation throughout the course.
