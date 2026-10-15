# LangChain + Pinecone Quickstart

This repository demonstrates how to build a simple semantic search / retrieval‑augmented generation (RAG) pipeline using **LangChain** with **Pinecone** as the vector store.  The goal is to let you prototype a question‑answering system with minimal setup while keeping all services free for experimentation and small‑scale application purposes.

---

## Overview of the Pipeline

1. **Document ingestion**  
   • Collections of text documents (plain `.txt`, `.pdf`, or other supported formats) are loaded using LangChain’s document loaders.

2. **Chunking**  
   • Large documents are split into short segments (≈ 1 k characters) to keep embeddings efficient and retrieval fast.

3. **Embedding**  
   • Each chunk is transformed into a numerical vector using a pre‑trained sentence‑embedding model (default `OpenAIEmbeddings`).  
   • The embedding model is free to use with the provided sandbox keys for small‑scale projects.

4. **Vector storage (Pinecone)**  
   • Vectors are stored in a Pinecone index.  Pinecone offers a **free tier** (1 GB of indexed data, 10 k queries/month) that is perfectly adequate for proof‑of‑concepts and low‑volume applications.  
   • The index is created automatically if it doesn’t exist.

5. **Similarity search**  
   • When a user submits a query, the same embedding model is used to embed the query vector.  
   • Pinecone retrieves the `k` most similar document chunks (cosine similarity).

6. **RAG with a language model**  
   • The retrieved content is fed into a prompt template and passed to a generative LLM (e.g., OpenAI’s ChatGPT or any other LLM that supports a simple completion API).  
   • The LLM outputs a concise answer tailored to the query and the retrieved context.

7. **Presentation**  
   • The final answer is returned to the user interface (Jupyter notebook cell, command‑line prompt, or a lightweight web UI).

---

## Free Service Highlights

| Service | Level | Key Points |
|---------|-------|------------|
| **Pinecone** | Free tier | 1 GB index, 10 k queries/month; no cost for small projects |
| **Embeddings** | Free open source model | HuggingFace have numerious open source models |
| **LLM / Chat** | Free LLMs | Ollama have numerious LLMs available for experimentation|
| **LangChain** | Open‑source | No cost, full developer control |
| **Pinecone** | Open‑source and free account cota| Free for small project |


> **Note:** While all services are free for modest usage, be mindful of the rate limits and data‑residency policies.  For production workloads consider the paid plans or self‑hosted alternatives.

---
## Project Setup

```bash
pinecone = "^7.3.0"
langchain = "^1.4.4"
langchain-ollama = "^1.1.0"
langchain-huggingface = "^1.2.3"
langchain-text-splitters = "^1.1.3"
sentence-transformers = "^6.1.0"
langchain-pinecone = "^0.2.13"
```
---

## Getting Started

1. Clone the repo and create a Python virtual environment.  
2. Use the toml file to create a venv having all required packages. 
3. Populate a `.env` file with your API keys for OpenAI and Pinecone.  
4. Place your source documents in the `data/` folder.  
5. Run the Jupyter notebook `quickstart_langchain_pinecone.ipynb`.  

The notebook walks you through all steps: indexing, querying, and generating answers.

---

## Next Steps

- Replace the embedding or LLM provider with alternatives (Cohere, Anthropic, Gemini).  
- Persist the Pinecone index across sessions.  
- Wrap the pipeline in a simple Flask app or Gradio UI for a public demo.  
- Add PDF or Markdown loaders to broaden the document types you can ingest.

---

Enjoy building your own AI‑powered retrieval system on a completely free stack!