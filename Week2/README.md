# Week 2 — RAG (Retrieval-Augmented Generation)

Learn how to ground LLM responses in your own documents using RAG.

## Prerequisites

- Week 1 completed (Ollama running, LangChain installed)
- Additional packages: `pip install langchain-community chromadb pypdf`

---

## Notebooks

| # | Notebook | Topic |
|---|----------|-------|
| 2.1 | `2.1_what_is_rag.ipynb` | What RAG is and why it solves LLM hallucination |
| 2.2 | `2.2_document_loading_chunking.ipynb` | Load PDFs & text files, split into chunks |
| 2.3 | `2.3_embeddings.ipynb` | Convert text to vectors, measure semantic similarity |
| 2.4 | `2.4_vector_stores.ipynb` | Store and search embeddings with Chroma |
| 2.5 | `2.5_basic_rag_pipeline.ipynb` | End-to-end RAG: load → embed → retrieve → generate |
| 2.6 | `2.6_conversational_rag.ipynb` | RAG with chat history for follow-up questions + Gradio UI |

---

## RAG Architecture

```
Your Documents
     ↓
  Chunking          split into smaller pieces
     ↓
  Embedding         convert text → vectors (OllamaEmbeddings)
     ↓
  Vector Store      save vectors in Chroma (searchable)
     ↓
  User Query  →  Retrieve top-k similar chunks
                      ↓
               Prompt = context + question
                      ↓
               LLM generates a grounded answer
```

## Key Concepts

- **Chunking** — split documents into smaller pieces with overlap
- **Embeddings** — numerical representation of text meaning
- **Vector Store** — database for fast similarity search (Chroma)
- **Retriever** — finds the most relevant chunks for a query
- **Semantic Search** — find documents by meaning, not keywords
- **Conversational RAG** — rephrase follow-up questions before retrieving

## Running the Notebooks

1. Start Ollama: `ollama serve`
2. Ensure model is available: `ollama pull llama3.2`
3. Install extra deps: `pip install langchain-community chromadb pypdf`
4. Run notebooks top to bottom
