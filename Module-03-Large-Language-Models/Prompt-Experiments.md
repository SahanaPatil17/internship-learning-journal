# Prompt Experiments for session 1

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
