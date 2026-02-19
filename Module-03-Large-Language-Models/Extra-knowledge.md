## FastAPI – Basic Concepts Overview

This video introduced the fundamentals of FastAPI, a modern and high-performance Python framework used to build APIs quickly and efficiently.

I learned how to install FastAPI and Uvicorn using pip and how to run a FastAPI application using the `uvicorn filename:app --reload` command. I understood how to create a basic API by initializing a FastAPI app and defining endpoints using decorators like `@app.get()`.

The video explained the main HTTP methods:
- GET – Retrieve data  
- POST – Create new data  
- PUT – Update existing data  
- DELETE – Remove data  

I learned about Path Parameters, which allow dynamic values inside the URL, and Query Parameters, which pass additional data using the `?key=value` format. I also understood the difference between required and optional parameters.

The concept of Request Body was introduced using Pydantic models to validate and structure incoming data when creating new records with the POST method. I also learned how to safely update existing data using optional fields in the PUT method and how to delete records using the DELETE method.

Finally, the video demonstrated FastAPI’s automatic interactive documentation available at `/docs`, which allows testing APIs directly from the browser.

Overall, this video helped me understand the core structure of building REST APIs using FastAPI, including routing, parameter handling, data validation, CRUD operations, and API documentation.

---

## Text Embeddings & Semantic Search – Concept Overview

This video explained how Transformer models represent text as numerical vectors called **embeddings** and how these embeddings can be used to perform **semantic search**.

Text embeddings convert sentences into high-dimensional vectors (arrays of numbers). Encoder-based models like BERT generate these vectors. Each token (word) in a sentence gets its own embedding, but since we usually need a single vector for the entire sentence, a technique called **pooling** is used.

Two common pooling methods:
- CLS token pooling – using the special classification token embedding  
- Mean pooling – averaging all token embeddings (excluding padding tokens using attention masks)

Once we obtain a single embedding per sentence, we can measure similarity between sentences using **cosine similarity**, which calculates the angle between two vectors. A higher cosine similarity score means the sentences are more semantically similar.

This idea can be extended to **semantic search**, where:
- All documents in a dataset are converted into embeddings  
- A query is embedded  
- Similarity scores are computed between the query and all documents  
- The most similar documents are retrieved  

To efficiently find the closest embeddings, tools like **FAISS (Facebook AI Similarity Search)** are used to perform fast nearest-neighbor search in high-dimensional space.

Overall, this video helped me understand how embeddings represent meaning numerically, how cosine similarity measures semantic closeness, and how semantic search systems retrieve relevant documents using embedding vectors.
