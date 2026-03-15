# Week 2 — RAG (Retrieval-Augmented Generation)

Learn how to ground LLM responses in your own documents using RAG — from basic pipelines to advanced retrieval and evaluation.

## Prerequisites

- Week 1 completed (Ollama running, LangChain installed)
- Additional packages: `pip install langchain-community chromadb pypdf rank_bm25`

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
| 2.7 | `2.7_advanced_retrieval.ipynb` | MMR, BM25, Hybrid Search, and LLM Reranking |
| 2.8 | `2.8_rag_evaluation.ipynb` | Evaluate RAG quality: Faithfulness, Relevance, Recall, Precision |

---

## RAG Architecture

```
Your Documents
     ↓
  Chunking          split into smaller pieces (RecursiveCharacterTextSplitter)
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

---

## Advanced Retrieval (2.7)

| Technique | Problem it solves |
|-----------|------------------|
| **Standard Similarity** | Baseline — finds top-k most similar chunks |
| **MMR** (Maximal Marginal Relevance) | Removes redundant/duplicate chunks |
| **BM25** (Keyword Search) | Catches exact keyword/name/number matches |
| **Hybrid Search** (BM25 + Semantic) | Best of both worlds |
| **LLM Reranking** | Re-scores candidates for precision |

Recommended production setup:
```
Hybrid (BM25 + Semantic) → Retrieve top-8 → Rerank → Take top-3 → LLM
```

---

## RAG Evaluation (2.8)

| Metric | Question it answers | Fix if low |
|--------|--------------------|----|
| **Faithfulness** | Is the answer grounded in context? | Tighten prompt, lower temperature |
| **Answer Relevance** | Does the answer address the question? | Improve prompt instructions |
| **Context Recall** | Did we retrieve the right chunks? | Tune chunk size, use hybrid search |
| **Context Precision** | Are retrieved chunks all useful? | Reduce `k`, add reranking |

---

## Key Concepts

- **Chunking** — split documents into smaller pieces with overlap so context is not lost
- **Embeddings** — numerical representation of text meaning (semantic similarity)
- **Vector Store** — database optimised for fast similarity search (Chroma)
- **Retriever** — finds the most relevant chunks for a query
- **Semantic Search** — find documents by meaning, not exact keywords
- **MMR** — diversify retrieved results to avoid redundancy
- **BM25** — classical keyword ranking, great for exact matches
- **Hybrid Search** — combine semantic + keyword search with weighted scoring
- **LLM Reranking** — use the LLM itself to re-score and re-order retrieved chunks
- **Conversational RAG** — rephrase follow-up questions before retrieving
- **RAG Evaluation** — measure pipeline quality with Faithfulness, Relevance, Recall, Precision

---

## Files in this Folder

| File | Description |
|------|-------------|
| `Gita.pdf` | Bhagavad Gita — used in Homework 1 |
| `Bible.pdf` | The Bible — used in Homework 1 |
| `employee_handbook.txt` | Sample HR document used across notebooks |
| `handbook.txt` | Shorter handbook variant |

---

## Homework

| # | File | Task |
|---|------|------|
| HW1 | `../homework/Week2_Homework1.txt` | Build a RAG system on the Bhagavad Gita or Bible |

---

## Running the Notebooks

1. Start Ollama: `ollama serve`
2. Ensure model is available: `ollama pull llama3.1`
3. Install extra deps: `pip install langchain-community chromadb pypdf rank_bm25`
4. Run notebooks in order: 2.1 → 2.2 → ... → 2.8
