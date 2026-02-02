---
title: "AI Basic Terminology Explained (Beginner-Friendly)"
date: 2026-02-02
categories: [AI, LLM, Basics]
tags: [ai, llm, rag, langchain, ollama]
---

## 🎯 Who This Is For

This document is written for **absolute beginners to AI**.

No math, no buzzwords, no assumptions.
The goal is to understand **what each term means** and **how everything fits together**.

---

## 1. What Is an LLM?

**LLM** stands for **Large Language Model**.

An LLM is an AI model trained on a huge amount of text so it can:

- Understand natural language
- Answer questions
- Summarise or explain content
- Generate human-like text

### Common LLM Examples

- GPT
- Llama
- Mistral
- Claude
- DeepSeek

> 💡 Think of an LLM as a **very advanced text prediction engine**.

---

## 2. Hardware: Where AI Runs

AI models run on hardware that can process large numbers efficiently.

- **CPU** – General-purpose processor (slow for AI)
- **GPU** – Optimised for parallel math (most common for AI)
- **NPU** – Specialised AI chip (mobile & edge devices)

> Most AI workloads today run on **GPUs**.

---

## 3. AI Workflow & UI Tools

These tools help you **build and interact with AI systems**.

### Workflow / Automation Tools

- **n8n**
- **Flowise**

Used to visually connect steps such as:  User Input → Retriever → LLM → Output


### UI Tools 

- **Streamlit**
- **Gradio**

Used to build:
- Simple web apps
- Chat interfaces
- Input/output dashboards

---

## 4. AI Frameworks (The Glue)

Frameworks connect LLMs, data, retrieval, and prompts.

### Popular Frameworks

- **LangChain**
- **LangGraph**
- **LlamaIndex**

They provide reusable building blocks so you don’t have to build everything from scratch.

---

## 5. Running LLMs Locally

### Runtime

- **Ollama**  
  Runs LLMs locally on your machine as a local server.

### Wrapper

- **ChatOllama**  
  A LangChain wrapper that allows Python to communicate with Ollama.

> **Runtime** = where the model runs  
> **Wrapper** = how your code talks to it

---

## 6. Prompt and Query

This is how humans talk to LLMs.

- **Prompt** – Instructions to the model  
  Example:
  > You are an assistant that answers using the provided context.

- **Query** – The user’s actual question  
  Example:
  > What is tokenization?

The final input usually looks like: Prompt + Retrieved Context + User Query


---

## 7. Source Data

LLMs **do not know your private data**.

Source data can include:

- Excel files
- PDFs
- Text documents
- Web pages
- Databases

To use this data, it must be **processed and indexed first**.

---

## 8. Tokenization (Core Concept)

### What Is Tokenization?

**Tokenization** breaks text into smaller units called **tokens**.

Example:
""" 
"The cat sat on the mat"
→ ["The", "cat", "sat", "on", "the", "mat"]
"""


Why this matters:

- Models cannot process raw text
- They only understand numbers
- Tokenization is the first step

---

## 9. Vectorization vs Embedding

### Vectorization

- Converts tokens into numbers
- Required for neural networks

### Embedding

An **embedding** is a numerical vector that represents **meaning**.

- Similar meanings → vectors close together
- Different meanings → vectors far apart

Example:

- "king" ≈ "queen"
- "king" ≠ "car"

> 💡 Embeddings enable **semantic search**, not just keyword matching.

---

## 10. Embedding Models

Embedding models automatically:

1. Tokenize text
2. Convert it into numeric vectors

### Popular Embedding Options

- HuggingFace Embeddings
- Sentence Transformers
- OpenAI Embeddings

You usually don’t handle tokenization manually — the model does it internally.

---

## 11. Vector Databases (Vector DB)

A **Vector DB** stores embeddings and allows fast similarity search.

### Common Vector Databases

- **FAISS** (local, lightweight)
- **Pinecone**
- **Weaviate**

Why they exist:

- Searching vectors directly is slow
- Vector DBs index vectors efficiently

---

## 12. Keyword Search vs Semantic Search

### Keyword-Based Retrieval

- **BM25**
- **TF-IDF**

How it works:

- Tokenizes text
- Matches keywords
- Scores relevance

Limitation:

- Does not understand meaning

---

### Semantic Retrieval

- Uses embeddings + vector databases
- Finds meaning, not exact words

Example:

> “How do I install Python?”  
> matches  
> “Python setup guide”

---

## 13. What Is RAG?

**RAG** stands for **Retrieval-Augmented Generation**.

It improves LLM answers by **feeding relevant data into the model**.

### RAG Has Two Components

#### Retriever

- Searches documents
- Returns relevant text chunks

#### Generator

- An LLM (GPT, Mistral, Llama)
- Generates answers using retrieved content

> RAG is a **design pattern**, not a single tool.

---

## 14. Why LangChain Is Popular for RAG

LangChain provides:

- Document loaders (Excel, PDF, web)
- Text splitters
- Embedding integrations
- Vector database support
- Keyword & semantic retrievers
- Prompt templates
- LLM integrations
- Chains (pipelines)
- Streamlit / FastAPI support

---

## 15. High-Level RAG Flow

![image.png](attachment:6357aa1d-ca90-4f0b-83d0-159698e1ad0f:image.png)

User Question
   |
   v
Retriever (BM25 / FAISS)
   |
   v
Relevant Documents
   |
   v
Prompt + Context
   |
   v
LLM (via Ollama)
   |
   v
Answer



---

## 16. How Everything Fits Together

| Step | Component | Purpose |
|----|----|----|
| Tokenization | BM25 / Embedding Model | Break text into tokens |
| Embedding | HuggingFace / Sentence Transformers | Convert meaning into vectors |
| Storage | FAISS | Store vectors efficiently |
| Retrieval | BM25 / FAISS | Find relevant chunks |
| Generation | LLM (Ollama) | Generate answers |
| UI | Streamlit | Display results |

---

## 17. Final Summary

- **LLMs** generate text but don’t know your data
- **Tokenization** breaks text into pieces
- **Embeddings** capture meaning as vectors
- **Vector DBs** store embeddings for fast search
- **RAG** = retrieval + generation
- **LangChain** connects all components
- **Ollama** runs LLMs locally
- **Streamlit** provides a UI



