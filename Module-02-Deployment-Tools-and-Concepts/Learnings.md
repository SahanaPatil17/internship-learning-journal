# Week 2 - Session 1

## 1. Containers Provide Isolation

Each container behaves like an independent mini-computer.

---

## 2. Image vs Container

Image → Blueprint  
Container → Running instance  

---

## 3. Port Binding Is Essential

Without port binding:
Browser cannot access container services.

---

## 4. Volume Mounting Prevents Data Loss

Container deleted ≠ Data deleted (if mounted)

This is critical for production systems.

---

## 5. Containers Can Communicate

Using custom networks, containers can:
- Share data
- Make API calls
- Work like microservices

---

## 6. Running LLM Locally Is Possible

We:
- Installed Ollama
- Installed Gemma model
- Generated responses offline

No OpenAI API key required.

---

## 7. Flask + LLM = Real AI Backend

We built:
- Input form
- AI text formatter
- Email generator
- Style transformer

---

## 8. Real-World Architecture Insight

This mirrors industry systems:
- Frontend container
- Backend container
- Model container
- Network bridge

---

## Overall Understanding

This session strengthened my understanding of:
- Container lifecycle
- Networking concepts
- Port mapping
- Volume management
- Microservice-style architecture
- AI integration in backend systems


---

# Week 2 – Session 2 

## Technical Learnings

- Understood difference between Containers and Virtual Machines
- Learned Podman vs Docker concepts
- Deployed static content using GitHub Pages
- Built APIs using FastAPI
- Understood GET and POST clearly
- Tested APIs using Swagger documentation
- Deployed backend using Vercel
- Understood serverless limitations
- Observed 504 timeout behavior
- Used ngrok for local tunneling
- Learned secure usage of environment variables
- Understood CORS configuration

---

## Key Concepts

- Containers are lightweight and share host kernel
- Serverless platforms run functions, not persistent servers
- Free Vercel plan limits execution to 300 seconds
- API keys must never be exposed in public repositories
- ngrok helps expose local servers publicly
- CORS protects backend from unauthorized origins

---

## Challenges Faced

- Understanding async behavior in FastAPI
- Differentiating UV and Uvicorn
- Handling `.env` file in Git
- Understanding Vercel limitations
- Clarifying CORS functionality

---

## Reflection

This session strengthened my understanding of backend API development and deployment workflow. I learned practical implementation of building, testing, securing, and deploying APIs in a real-world environment.
