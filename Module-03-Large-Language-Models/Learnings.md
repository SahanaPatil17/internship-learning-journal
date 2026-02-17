# Session 1

---

## Deeper Understanding of LLMs

- Learned that LLMs are probabilistic models.
- Understood tokenization and vector representation.
- Gained clarity on self-attention mechanism.

---

## Importance of Context

- Context window limits model memory.
- Hallucination often results from context loss.
- RAG helps overcome this limitation.

---

## Practical Use of Embeddings

- Learned how embeddings enable semantic similarity.
- Understood how vector databases scale large datasets.
- Realized importance in search engines and AI assistants.

---

## RAG & Hybrid Search

- Learned how retrieval improves answer accuracy.
- Understood combining keyword + vector search.
- Recognized enterprise relevance.

---

## Multimodal AI Awareness

- Learned how images and audio are processed.
- Understood Base64 encoding necessity.
- Realized real-world applications in surveillance and safety.

---

## Prompt Engineering Insight

Major takeaway:
Prompt quality directly affects output quality.

Understood:
- Structured prompting
- Schema-based output
- Need for documentation
- Model-specific tuning

---

## Structured Extraction Skills

- Learned how to convert unstructured text into JSON.
- Understood schema enforcement.
- Recognized commercial applications in invoice automation.

---

## Function Calling Understanding

- Learned how LLMs extract parameters.
- Understood backend function triggering.
- Realized how intelligent assistants are built.

---

## Production-Level Thinking

- Learned importance of:
  - Model evaluation
  - Cost comparison
  - Regression testing
- Understood how commercial AI systems are maintained.

---

## Overall Growth

Module 3 expanded my understanding from:

"Using AI APIs"  
to  
"Designing scalable AI systems".

I now understand how to architect intelligent, production-ready AI applications.

# Session 2

---

## Practical Understanding of Embeddings

I understood how embeddings are actually generated using APIs and how they represent semantic meaning numerically.

I learned how cosine similarity works mathematically using:
- Dot product
- Norm
- Vector normalization

---

## Implementing Similarity Search

I learned how to:
- Compare two sentences using embeddings.
- Compare text and image embeddings.
- Interpret similarity scores.

This clarified how semantic search works internally.

---

## API & Environment Handling

I understood:
- How to export environment variables.
- How .bashrc makes variables persistent.
- How incorrect endpoints cause API errors.
- Importance of correct proxy URLs.

---

## Multimodal Understanding

I learned how text and images can share the same embedding space.

This helped me understand:
- Cross-modal retrieval
- How image search engines work
- How Project 1 may require multimodal processing

---

## Real RAG Implementation

This session helped me clearly understand:

- Why chunking is required.
- Why embeddings must be stored.
- Why we sort by similarity.
- Why we only retrieve Top-K results.

I now understand the retrieval step of RAG clearly.

---

## Cost & Efficiency Awareness

Major takeaway:

- Never recompute embeddings repeatedly.
- Compute once, reuse multiple times.
- Reduce API cost.
- Optimize performance.

This session helped me think like a system designer, not just a coder.

---

## Debugging & Error Handling

I observed and understood:

- 404 errors due to wrong endpoint.
- JSON serialization issues.
- Timeout problems.
- Async vs sync behavior.
- Token expiration issues.

This improved my debugging confidence.

---

## Overall Outcome

This session significantly improved my practical understanding of:

- Embedding pipelines
- Similarity search
- RAG architecture
- Cost optimization
- Real-world AI system workflows

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

---

## Overall Prompt & Retrieval Insights

- Retrieval quality depends on embeddings.
- Chunk size affects accuracy.
- Sorting ensures relevance.
- Structured storage enables scalable systems.
- Proper API usage avoids unnecessary cost.

---

## Conclusion

This session strengthened my understanding of building a working retrieval pipeline using embeddings, chunking, similarity search, and efficient API usage — forming the foundation for a production-ready RAG system.
