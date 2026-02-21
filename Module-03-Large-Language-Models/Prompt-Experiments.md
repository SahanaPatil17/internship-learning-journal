# Session 1

This file documents prompt experimentation and observations during Module 3.

---

## Experiment 1 – Basic Prompt

Prompt:
"What is RAG?"

Observation:
- Response was correct but generic.
- Lacked structured clarity.
- No technical depth.

Learning:
Basic prompts produce high-level summaries only.

---

## Experiment 2 – Structured Prompt

Prompt:
"Explain Retrieval Augmented Generation (RAG) in 4 sections:
1. Problem it solves
2. How it works
3. Advantages
4. Real-world applications"

Observation:
- Output became structured.
- Sections clearly separated.
- Better explanation depth.

Learning:
Explicit structure improves output quality.

---

## Experiment 3 – JSON Output Enforcement

Prompt:
"Extract name, email and phone number from the following text.
Return output strictly in JSON format."

Observation:
- Model returned structured JSON.
- Occasionally added explanation outside JSON.

Fix:
Added:
"Do not include any text outside JSON."

Result:
Clean structured response.

---

## Experiment 4 – Role Assignment

Prompt:
"You are an AI system architect. Explain how to implement RAG in an enterprise system."

Observation:
- Response became more technical.
- Included workflow-level thinking.
- Higher quality reasoning.

Learning:
Assigning role improves contextual response quality.

---

## Experiment 5 – Constraint-based Prompt

Prompt:
"Explain embeddings in less than 100 words using simple language."

Observation:
- Output was concise.
- Clear and simplified.
- Followed constraint correctly.

Learning:
Clear constraints improve consistency.

---

## Experiment 6 – Function Calling Style Prompt

Prompt:
"Extract origin city, destination city, and date from the sentence:
'I want to travel from Bangalore to Delhi next Friday.'"

Observation:
- Model extracted parameters correctly.
- Suitable for backend function input.

Learning:
LLMs can convert natural language into structured parameters.

---

## Overall Prompt Engineering Insights

- Specific > Generic
- Structured > Paragraph format
- Explicit constraints reduce hallucination
- JSON schemas ensure automation-ready output
- Prompts must be documented for consistency

---

## Conclusion

Prompt experimentation is essential for:

- Building reliable AI systems
- Reducing inconsistencies
- Optimizing cost and performance
- Preparing models for production deployment

# Session 2 

This session involved experimentation with embeddings and retrieval-based questioning.

---

## Experiment 1 – Semantic Similarity

Compared:

- "apple" & "orange"
- "apple" & "lightning"

Observation:
- Similar objects had higher cosine similarity.
- Unrelated words had lower similarity.

Learning:
Embeddings capture semantic meaning, not just keywords.

---

## Experiment 2 – Multimodal Matching

Compared:

- Image of cat ↔ Text "cat"
- Image of cat ↔ Text "box"

Observation:
- Correct cross-modal similarity detected.
- Low similarity for unrelated objects.

Learning:
Multimodal embeddings enable cross-modal understanding.

---

## Experiment 3 – Chunk-Based Retrieval

Question:
"What is the purpose of TypeScript?"

Process:
- Generate embedding for question.
- Compare with stored chunk embeddings.
- Sort by similarity.
- Retrieve Top-5.

Observation:
- Correct documentation file ranked highest.
- Retrieval accurately identified relevant section.

Learning:
Similarity sorting is essential for RAG.

---

## Experiment 4 – Boolean Operator Question

Question:
"Which operator converts a value into explicit boolean?"

Observation:
- Correct document retrieved.
- Relevant markdown section identified.

Learning:
RAG can pinpoint exact documentation sections.

---

## Experiment 5 – Cost Optimization

Initial mistake:
- Recomputing embeddings repeatedly.

Improvement:
- Store embeddings once.
- Reuse stored vectors.
- Compute question embedding only once.

Learning:
Efficiency matters in production systems.

This session strengthened my understanding of building a working retrieval pipeline using embeddings, chunking, similarity search, and efficient API usage — forming the foundation for a production-ready RAG system.


## Session 3 

### Experiment 1: Forcing LLM to Respond “Yes”

Initial Approach:
- Direct instruction: “Reply only with yes.”
Result:
- Inconsistent output.

Improved Approach:
- Assigned role-based constraints.
- Framed system instruction.
- Added conditional formatting instructions.
- Used reinforcement in prompt structure.

Observation:
LLMs respond differently based on:
- Context framing
- Role definition
- Instruction clarity
- Constraint enforcement

Key Insight:
Prompt engineering is about behavioral control, not syntax.

---

### Experiment 2: API Token Troubleshooting

Steps Tested:
- Switched between AI Pipe and AI Proxy.
- Verified environment variable loading.
- Replaced base URL correctly.
- Restarted server after updating tokens.

Findings:
Errors were caused by:
- Wrong base endpoint
- Missing token in environment
- Token not exported properly

Lesson:
Environment setup must be validated before debugging logic.

---

### Experiment 3: FastAPI Deployment Validation

Steps:
- Verified local endpoint
- Tested deployed URL
- Compared JSON structure
- Checked headers
- Reviewed authentication settings

Observation:
Even valid JSON may fail if:
- Key names mismatch
- Extra wrapper object exists
- Content type incorrect
- Authentication blocking request

Lesson:
Strict format compliance is essential in automated evaluation systems.

---

### Experiment 4: Network Debugging

Used:
- Chrome DevTools Network tab
- Response preview
- Status code inspection
- Header validation

Common Issues Identified:
- 403 Forbidden (authentication issue)
- 401 Unauthorized (token issue)
- 500 Internal Server Error (logic/config issue)

Lesson:
Backend debugging requires systematic validation of request-response cycle.

## Session 4 

### Chat Completion Experiment
- Built a chatbot using Chat Completion API.
- Passed role-based messages (developer, user, assistant).
- Maintained conversation history manually.
- Extracted only the required `content` field from JSON response.

Observation: LLMs rely entirely on provided message history for context.

---

### Embedding & Similarity Experiment
- Generated embedding vectors using embedding API.
- Compared vectors using cosine similarity.
- Tested similarity between related and unrelated words.
- Verified that higher cosine similarity indicates stronger semantic relation.

Observation: Distance and cosine similarity behave differently (minimize distance, maximize cosine).

---

### Base64 Image Encoding
- Converted image → binary → Base64 string.
- Reconstructed Base64 → binary → image.
- Verified no data loss.

Observation: Base64 is essential for sending images through APIs.

---

### Multimodal Embedding Experiment
- Generated embeddings for both text and images.
- Confirmed same-dimensional vectors are required for comparison.
- Tested similarity between image embedding and text embedding.

Observation: Multimodal models enable cross-modal semantic comparison.

---

### Function Calling Experiment
- Defined function schema with parameters.
- Used `tool_choice="required"`.
- Extracted structured fields: manufacturing date, expiry date, product name.
- Parsed JSON from `tool_calls` in response.

Observation: Function calling provides reliable structured output compared to free-text responses.

---

