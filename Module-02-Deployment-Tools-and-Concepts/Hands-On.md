# Week 2 - Session 1 

## Step 1: Install Podman (WSL Ubuntu)

sudo apt update
sudo apt install podman

---

## Step 2: Pull Jupyter Image

podman pull quay.io/jupyter/base-notebook

---

## Step 3: Run Jupyter Container

podman run -d \
-p 8888:8888 \
--name jupyter-server \
quay.io/jupyter/base-notebook

Access:
http://localhost:8888

---

## Step 4: Run with Volume Mount

podman run -d \
-p 8888:8888 \
-v ~/jupyter-work:/home/jovyan/work \
--name jupyter-server \
quay.io/jupyter/base-notebook

Now files persist locally.

---

## Step 5: Pull Ollama Image

podman pull docker.io/ollama/ollama

---

## Step 6: Run Ollama Container

podman run -d \
-p 11434:11434 \
--name ollama \
docker.io/ollama/ollama

---

## Step 7: Install Model

podman exec -it ollama ollama run gemma:270m

---

## Step 8: Create Network

podman network create ai-network

Run containers with:

--network ai-network

---

## Step 9: Flask Web App

Created:
- HTML form
- Flask backend
- API call to Ollama
- Styled response output

Hosted on:
http://localhost:5000

# Week 2 – Session 2 

## 1. Install Required Packages

Install FastAPI, Uvicorn, and dotenv:

pip install fastapi uvicorn python-dotenv

---

## 2. Create FastAPI Application

Create a file named `app.py`

from fastapi import FastAPI
import uvicorn

app = FastAPI()

@app.get("/")
def home():
    return {"message": "Hello World"}

@app.get("/items")
def get_items():
    return {"message": "Items endpoint working"}

if __name__ == "__main__":
    uvicorn.run(app, host="0.0.0.0", port=8000)

Run the server:

uvicorn app:app --reload

Open in browser:

http://127.0.0.1:8000  
http://127.0.0.1:8000/docs

---

## 3. Add POST Endpoint

Add this to `app.py`:

@app.post("/create")
def create_item(name: str):
    return {"created": name}

Test it in:

http://127.0.0.1:8000/docs

Click “Try it out”, enter a name, and execute.

---

## 4. Test Timeout Behavior (Vercel Limitation)

Add this endpoint:

import time

@app.get("/delay")
def delay():
    time.sleep(301)
    return {"message": "Completed"}

When deployed to Vercel (free plan), this will return:

504 Timeout Error

Because Vercel allows maximum 300 seconds execution.

---

## 5. Deploy to Vercel

Step 1: Create requirements.txt

fastapi
uvicorn
python-dotenv

Step 2: Create vercel.json

{
  "builds": [
    {
      "src": "app.py",
      "use": "@vercel/python"
    }
  ],
  "routes": [
    {
      "src": "/(.*)",
      "dest": "app.py"
    }
  ]
}

Step 3: Install Vercel CLI

npm install -g vercel

Login:

vercel login

Deploy:

vercel

---

## 6. Setup Environment Variables

Create a file named `.env`

SECRET_KEY=topsecret

Add `.env` to `.gitignore`

.env

Use it in Python:

import os
from dotenv import load_dotenv

load_dotenv()

secret = os.getenv("SECRET_KEY")
print(secret)

This prevents exposing secrets publicly on GitHub.

---

## 7. Use ngrok for Local Tunneling

Run FastAPI locally:

uvicorn app:app --reload

Then start ngrok:

ngrok http 8000

It will generate a public URL.

Share that URL to allow others to access your local API.

---

## 8. Add CORS Configuration

Add this to `app.py`:

from fastapi.middleware.cors import CORSMiddleware

app.add_middleware(
    CORSMiddleware,
    allow_origins=["http://localhost:3000"],
    allow_methods=["GET", "POST"],
    allow_headers=["*"],
)

This allows only specified origins to access your API.

---

## Hands-On Summary

- Built FastAPI application
- Implemented GET and POST methods
- Tested APIs using Swagger docs
- Deployed backend to Vercel
- Observed 504 timeout behavior
- Secured secrets using environment variables
- Shared local server using ngrok
- Implemented CORS configuration
