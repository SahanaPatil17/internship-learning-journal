# Week 2 – Session 2 Notes

## Containers vs Virtual Machines

### Virtual Machines
- Have their own operating system
- Have their own kernel
- Heavy in size
- Consume more RAM and CPU
- Slower startup time
- Fully isolated

### Containers
- Share host system kernel
- Lightweight
- Faster startup
- Use only required dependencies
- More portable
- Multiple containers can run on same system

### Main Difference

| Feature | Virtual Machine | Container |
|----------|----------------|------------|
| Kernel | Own kernel | Shared kernel |
| Resource Usage | High | Low |
| Speed | Slower | Faster |
| Size | Heavy | Lightweight |

---

## Podman vs Docker

- Both are container engines
- Commands are mostly similar
- Podman is open-source
- Docker traditionally runs as root
- Podman supports rootless mode
- CLI compatible with Docker

Root user = Superuser with full system access.

---

## GitHub Pages

GitHub Pages is used to host static websites.

It supports:
- HTML
- Markdown
- CSS
- JavaScript

### Steps to Deploy
1. Create repository
2. Go to Settings
3. Click on Pages
4. Select main branch
5. Save

GitHub generates a public URL.

Important:
- `index.html` is rendered by default
- Markdown may need conversion
- `_sidebar.md` can be used for navigation (when using static site generator)

---

## FastAPI Introduction

FastAPI is a modern framework used to build APIs.

### Why FastAPI?
- Supports asynchronous programming
- Handles multiple requests efficiently
- Automatically generates API documentation
- Faster than Flask in async environments

---

## Running FastAPI Locally

Example:

```python
from fastapi import FastAPI
import uvicorn

app = FastAPI()

@app.get("/items")
def get_items():
    return {"message": "Hello from FastAPI"}

if __name__ == "__main__":
    uvicorn.run(app, host="0.0.0.0", port=8000)
