# Week 1 — GenAI Training

An introduction to working with Large Language Models (LLMs) locally using Ollama and LangChain.

## Prerequisites

- [Ollama](https://ollama.com/) installed and running (`ollama pull llama3.2`)
- Python 3.9+
- Dependencies: `pip install langchain langchain-ollama gradio chromadb tiktoken transformers`

---

## Notebooks

| # | Notebook | Topic |
|---|----------|-------|
| 1.1 | `1.1 tokenization_explained.ipynb` | How LLMs tokenize text — BPE (GPT) and WordPiece (BERT) |
| 1.2 | `1.2 langchain_model_calling.ipynb` | Calling a local LLM with LangChain and ChatOllama |
| 1.3 | `1.3 llm_hyperparameters.ipynb` | Effect of `temperature`, `top_p`, `top_k`, and `max_tokens` |
| 1.4 | `1.4 ollama_basic_prompting.ipynb` | Basic prompting with Ollama directly |
| 1.5 | `1.5 prompt_engineering_langchain.ipynb` | Prompt templates and prompt engineering techniques |
| 1.6 | `1.6 conversational_ai.ipynb` | Stateful vs stateless chat, managing conversation history |
| 1.7 | `1.7 langchain_tools.ipynb` | Defining and binding tools (`@tool`) to an LLM agent |
| 1.8 | `1.8 langchain_chains.ipynb` | Building chains with the pipe operator, parallel chains, streaming |
| 1.9 | `1.9 pizza_hut_chatbot.ipynb` | End-to-end chatbot with Gradio UI — Pizza Hut ordering assistant |

---

## Key Concepts

- **Ollama** — Run open-source LLMs locally (no API key required)
- **LangChain** — Framework for building LLM-powered applications
- **Tokenization** — How text is split into tokens before being processed by an LLM
- **Hyperparameters** — Control creativity and randomness of model outputs
- **Conversational AI** — Maintaining chat history across multiple turns
- **Tools / Function Calling** — Let the LLM call external functions to retrieve data or take actions
- **Chains** — Compose multiple LLM calls and operations into a pipeline
- **RAG (Retrieval-Augmented Generation)** — Ground LLM responses in your own documents
- **Gradio** — Quickly build web UIs for AI applications

---

## Running the Notebooks

1. Start Ollama: `ollama serve`
2. Pull the model: `ollama pull llama3.2`
3. Launch Jupyter: `jupyter notebook`
4. Open any notebook and run cells top to bottom
