# Week 3 — AI Agents

Build autonomous agents that plan, use tools, remember context, and coordinate with other agents.

## Prerequisites

- Week 1 and Week 2 completed
- Ollama running with `llama3.1` pulled
- Additional packages: `pip install langgraph`

---

## Notebooks

| # | Notebook | Topic |
|---|----------|-------|
| 3.1 | `3.1_what_is_an_agent.ipynb` | Chain vs Agent, the ReAct loop (Thought → Action → Observation) |
| 3.2 | `3.2_agent_with_tools.ipynb` | Multi-tool agent — calculator, weather, unit converter, Wikipedia |
| 3.3 | `3.3_agent_memory.ipynb` | Short-term buffer memory and long-term vector store memory |
| 3.4 | `3.4_react_agent_from_scratch.ipynb` | Implement ReAct manually — parse Thought/Action/Observation from text |
| 3.5 | `3.5_langgraph_intro.ipynb` | LangGraph — state, nodes, conditional edges, streaming |
| 3.6 | `3.6_multi_agent_systems.ipynb` | Supervisor + Researcher + Writer agents working together |
| 3.7 | `3.7_rag_agent.ipynb` | RAG Agent — decides when to retrieve vs answer directly |
| 3.8 | `3.8_human_in_the_loop.ipynb` | Pause agent for human approval before risky actions |
| 3.9 | `3.9_research_agent.ipynb` | Capstone — full research agent that searches, writes, and saves reports |

---

## Agent Architecture

```
User Query
    ↓
Agent (LLM)
    ↓ thinks
  Which tool do I need?
    ↓ calls tool
Tool executes → returns result
    ↓ observes
Agent thinks again
    ↓
  Do I have enough to answer?
  No → call another tool
  Yes → return final answer
```

---

## Key Concepts

| Concept | Description | Notebook |
|---------|-------------|---------|
| **ReAct Loop** | Thought → Action → Observation cycle | 3.1, 3.4 |
| **Tool Selection** | LLM reads docstrings to pick the right tool | 3.2 |
| **Short-term Memory** | Conversation history as a message list | 3.3 |
| **Long-term Memory** | Facts stored in a vector store, recalled by similarity | 3.3 |
| **Window Memory** | Keep only the last N messages to manage context | 3.3 |
| **StateGraph** | LangGraph's way of modeling agent flow | 3.5 |
| **Conditional Edges** | Route to different nodes based on state | 3.5 |
| **ToolNode** | LangGraph's built-in node for executing tool calls | 3.5 |
| **Supervisor Pattern** | One orchestrator delegates to specialist workers | 3.6 |
| **RAG Agent** | Agent that uses vector search as one of its tools | 3.7 |
| **HITL** | Human-in-the-loop — pause for approval before risky actions | 3.8 |

---

## Progression (Week 1 → 2 → 3)

```
Week 1:  LLM + Tools + Chains
              ↓
Week 2:  LLM + Documents (RAG)
              ↓
Week 3:  LLM + Tools + Memory + Planning + Coordination
         = Autonomous Agents
```

---

## Homework

| # | Task |
|---|------|
| HW1 | Build a personal assistant agent with 3+ tools of your choice |
| HW2 | Build a RAG agent on the Gita or Bible (extends Week 2 HW) |
| HW3 | Build a 2-agent system: Researcher + Writer |

---

## Running the Notebooks

1. Start Ollama: `ollama serve`
2. Pull model: `ollama pull llama3.1`
3. Install: `pip install langgraph langchain-community chromadb`
4. Run notebooks in order: 3.1 → 3.2 → ... → 3.9
