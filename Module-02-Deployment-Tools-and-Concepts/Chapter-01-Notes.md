# Week 2 Session 1 – Containerization with Podman & Local LLM Integration

## 📌 Introduction to Containerization

Containerization is a method of packaging an application along with all its dependencies into a single unit called an **image**, which can run consistently on any system.

Instead of installing:
- Python
- Flask
- Required libraries
- Runtime dependencies

We package everything inside a container.

---

## 🐳 Podman Overview

Podman is an open-source container engine similar to Docker.

### Podman vs Docker

| Podman | Docker |
|---------|---------|
| Open source | Requires daemon |
| Rootless containers | Runs via Docker daemon |
| No background service | Background service required |

Commands are mostly similar.

---

## 📦 Important Terminologies

### 1️⃣ Image
- A blueprint/template
- Contains application + dependencies
- Example: Jupyter Image, Ollama Image

### 2️⃣ Container (Pod)
- Running instance of an image
- Acts like a mini isolated OS

---

## 🔁 Container Lifecycle Commands

| Action | Command |
|--------|----------|
| Pull image | `podman pull` |
| Run container | `podman run` |
| List running containers | `podman ps` |
| Stop container | `podman stop` |
| Start container | `podman start` |
| Remove container | `podman rm` |
| Remove image | `podman rmi` |

---

## 🔓 Port Binding

Containers are isolated by default.

To access services from the browser, we bind ports:

-p host_port:container_port

Example:
-p 8888:8888

This allows accessing Jupyter via:
http://localhost:8888

---

## 💾 Volume Mounting

Problem:
If a container is deleted → all internal data is lost.

Solution:
Mount a local directory.

-v local_folder:container_folder

Example:
-v ~/jupyter-work:/home/jovyan/work

Now:
- Files are stored in local machine
- Data persists even after container removal

---

## 🤖 Running Local LLM with Ollama

Ollama allows running Large Language Models locally.

Steps:
1. Pull Ollama container
2. Run container
3. Install a lightweight model (Gemma 3 – 270M)
4. Execute model inside container

Command:
ollama run gemma:270m

This enables fully offline LLM execution.

---

## 🌐 Networking Between Containers

By default:
Containers cannot communicate with each other.

Solution:
Create a custom network.

podman network create ai-network

Run containers with:
--network ai-network

Now:
- Jupyter container
- Ollama container

can communicate internally.

---

## 🧠 Flask + LLM Integration

We built a simple Flask web app that:

1. Accepts user input
2. Sends request to Ollama API
3. Receives formatted response
4. Displays output in browser

This simulates a real-world AI web backend.

---

## 🎯 Key Outcome of Week 2 - Session 1

We successfully:
- Ran Jupyter in container
- Mounted volumes
- Bound ports
- Installed local LLM
- Connected multiple containers
- Built AI-powered web app
