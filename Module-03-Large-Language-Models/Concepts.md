# Session 1

---

## API Keys & Proxy Architecture

- Access to LLM services requires API keys.
- AI Pipe provides a **proxy key**, not a direct OpenAI key.
- API requests must use the correct base URL.
- Proxy architecture allows:
  - Centralized billing
  - Model switching
  - Controlled access

---

## How LLMs Work

LLMs are built using the **Transformer architecture**.

Workflow:
1. Input text → Tokenization
2. Tokens → Vector embeddings
3. Self-attention applied
4. Probability distribution computed
5. Most likely next token generated

LLMs:
- Are not sentient.
- Perform matrix operations.
- Predict the next token probabilistically.

---

## Tokens & Context Window

- Text is broken into tokens (not always full words).
- Models charge based on token usage.
- Context window = Maximum tokens model can process at once.
- Small context → hallucination risk.
- Larger context → better reasoning capacity.

---

## Self-Attention

Self-attention helps determine:

- Which words relate to each other.
- Contextual references.
- Meaning disambiguation.

Example:
“The animal was tired because it ran.”
- “it” refers to “animal”.

Self-attention assigns probabilities to determine this relationship.

---

## Embeddings

Embeddings convert text into numerical vectors.

Uses:
- Semantic similarity
- Search engines
- Clustering
- Recommendation systems

Closer vectors → More similar meaning.

---

## Multimodal Embeddings

Different data types mapped into same vector space:

- Text
- Images
- Audio
- Video frames

Enables:
- Image search using text
- Audio understanding
- Cross-modal retrieval

---

## Vector Databases

When embeddings grow large, they must be stored efficiently.

Examples:
- ChromaDB
- LanceDB
- DuckDB
- PostgreSQL (vector extensions)

Purpose:
- Fast similarity search
- Efficient retrieval

---

## Retrieval Augmented Generation (RAG)

Problem:
LLMs forget context and hallucinate.

Solution:
1. Store documents externally.
2. Retrieve relevant chunks.
3. Inject into prompt.
4. Generate grounded response.

Benefits:
- Reduces hallucination
- Enables domain-specific AI
- Improves factual accuracy

---

## Hybrid RAG

Combines:
- Keyword search
- Vector similarity search

Ensures:
- Precision
- Semantic relevance

Tools like Typesense help implement this.

---

## Base64 Encoding

Used to send:
- Images
- Audio
- Binary files

Binary → Base64 text → Sent to API → Decoded.

Required because LLM APIs process text input.

---

## Vision Models

Videos = sequence of frames.

Applications:
- Exam monitoring
- Workplace safety
- Behavior detection
- Security systems

Key idea:
Send selected frames instead of entire video stream.

---

## Prompt Engineering

The most important skill in Module 3.

Key practices:
- Be explicit and structured.
- Use JSON/XML formatting.
- Separate instructions clearly.
- Document working prompts.

Better prompts → More consistent outputs.

---

## Structured Output & Schemas

To automate systems, LLM output must be structured.

Use schemas to:
- Define expected fields.
- Enforce JSON format.
- Avoid unstructured text responses.

Critical for:
- Invoice extraction
- Compliance automation
- Backend integration

---

## Function Calling

Allows LLM to:

- Extract structured parameters.
- Trigger backend functions.
- Execute workflows.

Example:
Travel assistant:
- Extract origin
- Extract destination
- Extract date
- Call booking API

Bridges natural language and backend systems.

---

## Agents & Tools

Tools:
- Defined callable functions.

Agents:
- Use reasoning + tools.
- Perform multi-step workflows.

---

## LLM Evaluation

Important for production systems.

Evaluate:
- Accuracy
- Cost
- Token usage
- Latency
- Regression issues

Use YAML-based testing and assertions.

---

## Summary

Module 3 shifts focus from:

Basic API calls → Intelligent, production-ready AI systems.

# Session 2

---

## Embeddings

Embeddings are numerical vector representations of text (or other data).

- Generated using models like:
  - text-embedding-3-small (OpenAI)
  - Sentence Transformers
- Used for:
  - Similarity search
  - Semantic matching
  - Retrieval systems
- Lower cost compared to chat models.

Similarity between vectors is calculated using:
- Cosine similarity
- Dot product
- Vector normalization (norm)

---

## Cosine Similarity

Used to measure semantic similarity between two embeddings.

Formula:
Similarity = (A · B) / (||A|| × ||B||)

- Value ranges from 0 to 1 (after normalization)
- Higher value = more similar

Example:
"apple" & "orange" → high similarity  
"apple" & "lightning" → low similarity  

---

## Environment Variables & API Usage

- API keys stored using environment variables.
- Can export using:
  - export KEY=value
  - .bashrc for persistence
- HTTPX used to send API requests.
- AI Pipe proxy endpoint used instead of direct OpenAI endpoint.

---

## Multimodal Embeddings

Multimodal models map:

- Text
- Images

into the same vector space.

This allows:
- Comparing image with text
- Cross-modal similarity search

Example:
Image of a cat ↔ Text "cute cat" → high similarity  
Image of cat ↔ Text "box" → low similarity  

Used Nomic AI API for generating multimodal embeddings.

---

## Vector Databases

Embeddings must be stored for large-scale retrieval.

Instead of recalculating embeddings repeatedly:
- Store them once
- Reuse for similarity comparison

Structure stored:
- ID (source file)
- Text content
- Embedding vector

---

## Chunking

Large documents cannot be sent fully due to token limits.

Solution:
- Split documents into chunks (e.g., 496 tokens each)
- Store embeddings per chunk

Why important:
- Avoid token overflow
- Improve retrieval accuracy
- Reduce API cost

---

## Building a Basic RAG Pipeline

Steps implemented:

1. Clone documentation (TypeScript docs)
2. Chunk markdown files
3. Generate embeddings for each chunk
4. Store in JSON collection
5. Compute similarity between question and stored embeddings
6. Sort by similarity
7. Retrieve Top-5 relevant chunks

Only top relevant chunks are used for answer generation.

---

## Cost Optimization

Important practices learned:

- Do not recompute embeddings unnecessarily
- Compute question embedding once
- Store embeddings permanently
- Avoid repeated API calls

---

## Async vs Sync API Calls

- Async can speed up bulk embedding generation.
- Timeout handling is important.
- JSON-safe handling required while saving responses.

---

## ask_question.py Workflow

Process:

- Load stored embeddings
- Generate embedding for user question
- Calculate similarity
- Sort results
- Retrieve top matches

This forms the retrieval part of a RAG system.

---

## Summary

This session moved from theory to implementation and demonstrated how to build a working retrieval system using embeddings, similarity search, and chunking.
