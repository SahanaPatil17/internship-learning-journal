# Week 2 – Session 3

## 1. GitHub Codespaces

GitHub Codespaces is a cloud-based development environment.

Instead of coding on your local machine, you develop directly in the cloud.

It provides:
- Linux-based virtual machine (Ubuntu)
- Configurable CPU & RAM
- Browser-based VS Code
- Cloud-hosted containers

### Key Features
- Preconfigured development environment
- Automatic setup using devcontainer.json
- Supports Docker
- Accessible from anywhere
- Auto shutdown after inactivity

### Free Usage
- 120 compute hours/month (Free account)
- 180 hours/month (Student Developer Pack)
- Usage depends on selected machine configuration

---

## 2. Dev Containers

Folder structure required:

.github/
.devcontainer/
    ├── devcontainer.json
    └── Dockerfile

### devcontainer.json

Used to:
- Define extensions
- Define settings
- Specify Dockerfile
- Install dependencies after container creation

### Dockerfile

Defines:
- Base image (e.g., Python 3.10)
- OS packages
- Installed libraries
- Working directory
- Copying files into container

Example base image:

FROM mcr.microsoft.com/devcontainers/python:3.10

---

## 3. Why Use Codespaces?

Use cases:
- Team collaboration
- Avoid installing dependencies locally
- Standardized environment
- Large enterprise projects
- Onboarding new developers quickly

---

## 4. Hugging Face Spaces

Hugging Face Spaces is used for deploying ML models and applications.

Platform:
https://huggingface.co

Features:
- Model hosting
- Dataset hosting
- App deployment
- Supports Docker
- Supports Gradio apps
- CPU and GPU options

### File Size Rules
- Large model files use Git LFS
- Supports files larger than 100MB

---

## 5. Deploying on Hugging Face Spaces

Steps:
1. Create a new Space
2. Choose Docker option
3. Create Dockerfile
4. Add requirements.txt
5. Add app.py
6. Push using Git

Deployment happens automatically after push.

---

## 6. Git LFS (Large File Storage)

Used when:
- Model files are large (GBs)
- Files exceed 100MB

Command:
git lfs install

---

## 7. GitHub Actions

GitHub Actions is used for automation.

Location:
.github/workflows/

File extension:
.yml or .yaml

### Purpose
- Run tests automatically
- Continuous Integration (CI)
- Continuous Deployment (CD)
- Scheduled tasks (cron jobs)
- Auto validation of pull requests

---

## 8. YAML Workflow Structure

Basic structure:

name: Test Workflow

on:
  workflow_dispatch:
  schedule:
    - cron: "0 12 * * *"

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Install dependencies
        run: pip install requests
      - name: Run script
        run: python script.py

---

## 9. CI/CD Concept

CI – Continuous Integration  
CD – Continuous Deployment

Purpose:
- Automatically test code on every push
- Prevent broken commits
- Ensure quality
- Automate deployment

Example:
- Run tests when someone pushes code
- Deploy app automatically after tests pass

---

## 10. Differences

Codespaces → Development environment  
Hugging Face Spaces → Deployment platform  
GitHub Actions → Automation engine  

All three serve different purposes.
