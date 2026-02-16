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
