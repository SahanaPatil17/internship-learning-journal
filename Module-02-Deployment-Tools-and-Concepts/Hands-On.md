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

# Week 2 – Session 3 

## 1. Create GitHub Codespace

Step 1:
Go to GitHub → Create new repository

Step 2:
Click Code → Create Codespace

Step 3:
Wait for cloud environment to start

---

## 2. Configure Dev Container

Create folder:

.devcontainer/

Create file:

devcontainer.json

Example:

{
  "name": "Python Dev",
  "build": {
    "dockerfile": "Dockerfile"
  },
  "extensions": [
    "ms-python.python"
  ],
  "postCreateCommand": "pip install -r requirements.txt"
}

---

## 3. Create Dockerfile

Inside .devcontainer/

Dockerfile:

FROM mcr.microsoft.com/devcontainers/python:3.10

WORKDIR /app
COPY . /app
RUN pip install fastapi uvicorn

---

## 4. Deploy on Hugging Face Spaces

Step 1:
Go to huggingface.co

Step 2:
Create new Space

Select:
Docker
CPU Basic
Public

Step 3:
Clone repository

git clone <space-url>

Step 4:
Create files:

requirements.txt

fastapi
uvicorn

app.py

from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def home():
    return {"message": "Hello World"}

Dockerfile

FROM python:3.10

WORKDIR /app
COPY . /app
RUN pip install -r requirements.txt

CMD ["uvicorn", "app:app", "--host", "0.0.0.0", "--port", "7860"]

Step 5:
Push to Hugging Face

git add .
git commit -m "Initial deployment"
git push

App gets deployed automatically.

---

## 5. Create GitHub Action

Create folder:

.github/workflows/

Create file:

test.yml

Example:

name: Sample Workflow

on:
  workflow_dispatch:

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Run command
        run: echo "Hello from GitHub Actions"

Push changes.

Go to GitHub → Actions → Run Workflow.

---

## 6. Create Scheduled Workflow

on:
  schedule:
    - cron: "0 12 * * *"

This runs daily at 12 PM.

# Week 2 – Session 4 

## 1. Install Required Packages

pip install fastapi uvicorn python-multipart pydantic python-dotenv

---

## 2. Create FastAPI Application

Create `app.py`

from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def home():
    return {"message": "Server Running"}

Run the server:

uvicorn app:app --reload

Open:

http://127.0.0.1:8000  
http://127.0.0.1:8000/docs

---

## 3. Add Path and Query Parameters

@app.get("/items/{item_id}")
def get_item(item_id: int):
    return {"item_id": item_id}

@app.get("/search")
def search(q: str):
    return {"query": q}

Test in Swagger docs.

---

## 4. Add POST Endpoint with Validation

from pydantic import BaseModel

class User(BaseModel):
    username: str
    email: str
    age: int

@app.post("/users")
def create_user(user: User):
    return {"user": user}

Test using Swagger UI.

---

## 5. Add File Upload

from fastapi import UploadFile, File

@app.post("/upload")
async def upload(file: UploadFile = File(...)):
    content = await file.read()
    return {"filename": file.filename}

Test using Swagger or curl.

---

## 6. Add Environment Variables

Create `.env`

SECRET_KEY=mysecret123

Add `.env` to `.gitignore`

.env

Load in app:

from dotenv import load_dotenv
import os

load_dotenv()
SECRET = os.getenv("SECRET_KEY")

---

## 7. Create requirements.txt

fastapi
uvicorn
python-multipart
pydantic
python-dotenv

---

## 8. Create Dockerfile

FROM python:3.11
WORKDIR /app
COPY . /app
RUN pip install -r requirements.txt
CMD ["uvicorn", "app:app", "--host", "0.0.0.0", "--port", "7860"]

---

## 9. Deploy to Hugging Face

1. Create new Space
2. Choose Docker
3. Upload app.py, Dockerfile, requirements.txt
4. Add SECRET_KEY in Settings
5. Deploy

---

## 10. Create Simple Test Script

Create `test.sh`

curl http://localhost:8000/
curl http://localhost:8000/items/1

Run:

bash test.sh

---

## Hands-On Summary

- Built FastAPI backend
- Implemented GET, POST, and file uploads
- Used Pydantic validation
- Secured secrets with .env
- Created Dockerfile
- Deployed to Hugging Face
- Automated testing with curl
