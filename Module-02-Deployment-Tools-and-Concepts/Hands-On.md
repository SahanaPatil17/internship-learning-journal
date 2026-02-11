# Week 2 - Session 1 

## 🛠 Step 1: Install Podman (WSL Ubuntu)

sudo apt update
sudo apt install podman

---

## 📥 Step 2: Pull Jupyter Image

podman pull quay.io/jupyter/base-notebook

---

## ▶ Step 3: Run Jupyter Container

podman run -d \
-p 8888:8888 \
--name jupyter-server \
quay.io/jupyter/base-notebook

Access:
http://localhost:8888

---

## 💾 Step 4: Run with Volume Mount

podman run -d \
-p 8888:8888 \
-v ~/jupyter-work:/home/jovyan/work \
--name jupyter-server \
quay.io/jupyter/base-notebook

Now files persist locally.

---

## 📥 Step 5: Pull Ollama Image

podman pull docker.io/ollama/ollama

---

## ▶ Step 6: Run Ollama Container

podman run -d \
-p 11434:11434 \
--name ollama \
docker.io/ollama/ollama

---

## 🧠 Step 7: Install Model

podman exec -it ollama ollama run gemma:270m

---

## 🌐 Step 8: Create Network

podman network create ai-network

Run containers with:

--network ai-network

---

## 🌍 Step 9: Flask Web App

Created:
- HTML form
- Flask backend
- API call to Ollama
- Styled response output

Hosted on:
http://localhost:5000
