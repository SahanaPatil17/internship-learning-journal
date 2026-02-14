# Week 2 – Session 4

## 1. TDS Project Workflow Overview

The complete TDS project architecture works as follows:

1. Student submits:
   - API Endpoint URL
   - GitHub Repository URL
   - Secret Key

2. TDS Server sends a JSON request to the API.

3. API must:
   - Immediately return HTTP 200 OK
   - Complete the task within 10 minutes

4. API processes the request:
   - Validates secret key
   - Generates application code
   - Creates GitHub repository
   - Deploys application
   - Sends structured JSON response back

---

## 2. FastAPI Fundamentals

### GET Request

Used to retrieve data.

@app.get("/")
def home():
    return {"message": "Hello World"}

---

### Path Parameters

Used when value is part of the URL.

@app.get("/items/{item_id}")
def get_item(item_id: int):
    return {"item_id": item_id}

---

### Query Parameters

Used for filtering and searching.

@app.get("/search")
def search(q: str):
    return {"query": q}

---

## 3. Data Validation using Pydantic

Pydantic ensures automatic validation.

from pydantic import BaseModel, EmailStr

class User(BaseModel):
    username: str
    email: EmailStr
    age: int

Benefits:
- Type checking
- Email format validation
- Required field enforcement
- Automatic error responses

---

## 4. POST Requests

Used to send structured JSON data.

@app.post("/users")
def create_user(user: User):
    return {"user": user}

POST requests are used for:
- Creating data
- Submitting JSON
- Sending payloads

---

## 5. File Upload Handling

### Single File Upload

from fastapi import UploadFile, File

@app.post("/upload")
async def upload(file: UploadFile = File(...)):
    content = await file.read()
    return {"filename": file.filename}

---

### Multiple File Upload

@app.post("/upload-multiple")
async def upload_files(files: list[UploadFile] = File(...)):
    return {"files": [file.filename for file in files]}

---

## 6. Testing APIs using curl

GET request:

curl http://localhost:8000/

POST request:

curl -X POST http://localhost:8000/users \
-H "Content-Type: application/json" \
-d '{"username":"test","email":"test@test.com","age":20}'

File upload:

curl -X POST http://localhost:8000/upload \
-F "file=@cars.json"

curl helps in automated testing and scripting.

---

## 7. Secret Key Handling

Secrets should not be hardcoded.

Create `.env` file:

SECRET_KEY=mysecret

Load it in Python:

from dotenv import load_dotenv
import os

load_dotenv()
secret = os.getenv("SECRET_KEY")

Why?
- Prevents exposing credentials
- Protects API keys
- Secure deployment practice

---

## 8. Docker Basics

Docker ensures consistent environment across machines.

Dockerfile example:

FROM python:3.11

WORKDIR /app
COPY . /app

RUN pip install -r requirements.txt

CMD ["uvicorn", "app:app", "--host", "0.0.0.0", "--port", "7860"]

Benefits:
- Standard runtime
- Easy cloud deployment
- Environment isolation

---

## 9. Deployment on Hugging Face

Steps:

1. Create new Space
2. Select Docker template
3. Upload:
   - app.py
   - requirements.txt
   - Dockerfile
4. Add secret key in Settings
5. Deploy

Default port: 7860

---

## 10. Automation using Bash Scripts

Automated scripts can test multiple endpoints quickly.

Example:

curl http://localhost:8000/
curl http://localhost:8000/items/1
curl http://localhost:8000/search?q=test

This reduces manual testing effort.
