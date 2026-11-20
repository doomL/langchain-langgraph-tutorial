<div align="center">

# LangChain × LangGraph Tutorial Series

**28 hands-on tutorials — from your first chain to production multi-agent systems**

[![Python](https://img.shields.io/badge/Python-3.11%2B-3776AB?style=flat&logo=python&logoColor=white)](https://www.python.org/)
[![LangChain](https://img.shields.io/badge/LangChain-1.x-1C3C3C?style=flat&logo=langchain&logoColor=white)](https://python.langchain.com/)
[![LangGraph](https://img.shields.io/badge/LangGraph-1.x-FF6B35?style=flat)](https://langchain-ai.github.io/langgraph/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat)](LICENSE)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebooks-F37626?style=flat&logo=jupyter&logoColor=white)](https://jupyter.org/)

<a href="https://groq.com" target="_blank" rel="noopener noreferrer">
  <img
    src="https://console.groq.com/powered-by-groq-dark.svg"
    alt="Powered by Groq for fast inference."
    width="180"
  />
</a>

</div>

---

## What's inside

This series takes you from the very basics of LangChain all the way to cutting-edge patterns like Corrective RAG, Deep Agents, and the MCP/A2A protocols. Every tutorial is a self-contained Jupyter notebook — read the theory, run the cells, and experiment.

| Phase | Tutorials | Topics |
|---|---|---|
| **Foundations** | 01 – 06 | LangChain core, prompts, chains, agents, RAG, memory |
| **LangGraph** | 07 – 13 | Graphs, complex flows, real-world apps, best practices |
| **Advanced patterns** | 14 – 21 | HITL, Supervisor, Swarm, Subgraphs, Parallelism, Memory, Time Travel, Functional API |
| **Cutting-edge** | 22 – 28 | Deep Agents, utilities, middleware, MCP & A2A, streaming, fault tolerance, decisions |

---

## New version update (November 2026)

Checked against **LangChain 1.5.2**, **LangGraph 1.2.24**, and **Deep Agents 0.7.41**.

The libraries moved. A notebook that still imported the old names would warn on import, or teach a call that no longer matches the docs. This update follows those moves. It also adds the three topics the series stopped short of: showing a run while it happens, keeping a thread alive when a node fails, and letting a decision model pick the chat model or refuse a tool.

Python **3.11+** is required. LangChain 1.5 and `langchain-core` 1.8 dropped 3.10.

### What moved

| Before | Now | Why |
|---|---|---|
| `create_react_agent` from `langgraph.prebuilt` | `create_agent` from `langchain.agents` | Deprecated since LangGraph 1.0. The supported factory is the LangChain 1.0 agent, and its prompt argument is `system_prompt`. `create_supervisor` still takes `prompt=`. Tutorials 4, 5, 11, 15, and 16. |
| `langchain-mcp-adapters` and `MultiServerMCPClient` | `langchain[mcp]` and `MCPAdapter` | LangChain 1.4 ships MCP inside `langchain.mcp`, on top of FastMCP. Tutorial 25 connects an in-process server, so the example runs without Node.js. The namespace is still beta. |
| `from langgraph.server import LangGraphServer` | `langgraph dev`, then `/a2a/{assistant_id}` | That class is not in the `langgraph` package. The Agent Server publishes the A2A card for each assistant. |
| `write_todos` on every deep agent | `middleware=[TodoListMiddleware()]` | Deep Agents 0.7 leaves planning off by default so a normal turn sends fewer tokens. The default tools are the filesystem, `execute`, and `task`. Tutorial 22. |
| `MemorySaver` | Same class, also named `InMemorySaver` | The old name still works. Tutorial 27 uses the current name. Older tutorials keep `MemorySaver`. |

### What was added

| Tutorial | Why it is here |
|---|---|
| **26 — Streaming** | `invoke()` returns one final state. A chat UI needs tokens, tool progress, and subgraph events while the run is going. `version="v2"` makes every chunk the same shape. |
| **27 — Fault tolerance** | LangGraph 1.2 can retry a node, cap one async attempt, compensate after the retries are gone, and stop between steps with `RunControl` without dropping the checkpoint. |
| **28 — Decision models** | LangChain 1.5 answers a typed question (`Noul`, `Choice`, `Score`) instead of a paragraph. `ModelRouterMiddleware` picks the model for a run. `AutoModeMiddleware` blocks a risky tool. The notebook uses a local classifier, so it does not need a TypeSafe key. |

Cells that call Groq still need `GROQ_API_KEY`. Tutorials 22 and 25 skip those cells when the key is missing. Tutorials 26, 27, and 28 run without one.

---

## Quick Start

### 1. Get a Groq API key

Groq provides **free, blazing-fast LLM inference** used throughout this series.

1. Go to **[console.groq.com](https://console.groq.com)**
2. Sign up (or log in) — no credit card required for the free tier
3. Navigate to **API Keys** → **Create API Key**
4. Copy the key — you'll use it in step 4 below

### 2. Clone and set up

```bash
git clone https://github.com/DoomL/langchain-langgraph-tutorial.git
cd langchain-langgraph-tutorial
```

```bash
# Create and activate virtual environment
python3 -m venv .venv
source .venv/bin/activate        # Linux / macOS
# .venv\Scripts\activate         # Windows
```

```bash
pip install -r requirements.txt
```

### 3. Configure your environment

Create a `.env` file in the repo root:

```plaintext
GROQ_API_KEY=your_groq_api_key_here

# Optional — enables LangSmith tracing
LANGCHAIN_TRACING_V2=false
LANGCHAIN_API_KEY=your_langsmith_key_here
LANGCHAIN_PROJECT=LangChainTutorial
```

### 4. Open any tutorial

```bash
jupyter notebook Tutorial01/Tutorial_1_Introduction_to_LangChain.ipynb
```

---

## Tutorial Map

### Foundations (Tutorials 1–6)

| # | Title | Key concepts |
|---|---|---|
| 01 | **Introduction to LangChain** | LCEL, chains, prompts, first app |
| 02 | **Working with Language Models** | `ChatGroq`, `PromptTemplate`, output parsers |
| 03 | **Document Processing** | Loaders, text splitting, FAISS, Corrective RAG (CRAG) |
| 04 | **Agents in LangChain** | `create_agent`, tool calling, multi-tool agents |
| 05 | **Advanced Agent Techniques** | Vector search tools, memory agents, research assistant |
| 06 | **Memory Systems** | `MemorySaver`, `InMemoryStore`, `add_messages`, summary memory |

### LangGraph (Tutorials 7–13)

| # | Title | Key concepts |
|---|---|---|
| 07 | **Introduction to LangGraph** | `StateGraph`, nodes/edges, `add_messages`, `ToolNode`, ReAct loop |
| 08 | **Complex Flows** | Conditional edges, `add_conditional_edges`, error handling |
| 09 | **Combining LangChain + LangGraph** | LCEL inside graphs, async optimisation, CRAG pipeline |
| 10 | **Real-world Applications** | Content moderation, translation, customer support chatbot |
| 11 | **Structured Data** | Pydantic, `.with_structured_output()`, JSON queries |
| 12 | **Advanced LangChain Techniques** | Custom chains, RAG, sentiment analysis |
| 13 | **Best Practices & Advanced Topics** | Async LCEL, token tracking, FastAPI deployment, Prometheus |

### Advanced Patterns (Tutorials 14–21)

| # | Title | Key concepts |
|---|---|---|
| 14 | **Human-in-the-Loop** | `interrupt()`, `Command(resume=...)`, approval workflows |
| 15 | **Supervisor Agent** | `create_supervisor()`, worker delegation, multi-level hierarchy |
| 16 | **Swarm Agents** | `create_swarm()`, peer-to-peer handoffs, `create_handoff_tool()` |
| 17 | **Subgraphs** | Nested graphs, shared vs private state, `Command.PARENT` |
| 18 | **Parallelization & Map-Reduce** | Fan-out/fan-in, `Send` API, conditional fan-out, stable sorting |
| 19 | **Long-term Memory** | `MemorySaver`, `SqliteSaver`, `InMemoryStore`, `trim_messages()` |
| 20 | **Time Travel** | `get_state_history()`, forking, `update_state()` |
| 21 | **Functional API** | `@entrypoint`, `@task`, `previous`, parallel tasks |

### Cutting-edge (Tutorials 22–25)

| # | Title | Key concepts |
|---|---|---|
| 22 | **Deep Agents** | `create_deep_agent()`, opt-in `TodoListMiddleware`, filesystem, sub-agents |
| 23 | **LangChain 1.0 Utilities** | `init_chat_model()`, `trim_messages()`, `filter_messages()` |
| 24 | **Agent Middleware** | `AgentMiddleware`, `before_model`, `after_model`, `wrap_model_call`, `HumanInTheLoopMiddleware` |
| 25 | **MCP & A2A Protocol** | `MCPAdapter`, in-process FastMCP, Agent Cards |
| 26 | **Streaming** | `stream_mode`, `version="v2"`, tokens, custom progress, subgraphs |
| 27 | **Fault Tolerance** | retries, `timeout`, `error_handler`, `RunControl` drain |
| 28 | **Decision Models** | `Noul`, `Choice`, `Score`, model routing, risky-tool blocking |

---

## Prerequisites

- **Python 3.11+** — required by LangChain 1.5 and `langchain-core` 1.8
- **Basic Python knowledge** — functions, classes, async/await
- **Jupyter Notebooks** — how to open and run cells
- **A Groq API key** — free at [console.groq.com](https://console.groq.com)

No prior LangChain experience required — Tutorial 1 starts from scratch.

---

## Project structure

```
langchain-langgraph-tutorial/
├── README.md
├── requirements.txt
├── .env                    ← create this (see Quick Start above)
├── Tutorial01/
│   ├── README.md
│   └── Tutorial_1_Introduction_to_LangChain.ipynb
├── Tutorial02/ …
│   ⋮
├── Tutorial25/
│   ├── README.md
│   └── Tutorial_25_mcp_a2a_protocol.ipynb
├── Tutorial26/
│   ├── README.md
│   └── Tutorial_26_streaming.ipynb
├── Tutorial27/
│   ├── README.md
│   └── Tutorial_27_fault_tolerance.ipynb
└── Tutorial28/
    ├── README.md
    └── Tutorial_28_decision_models.ipynb
```

---

## Models used

The series uses **[Groq](https://groq.com)** for fast LLM inference:

| Tutorial | Model |
|---|---|
| 01 – 13, 15 – 21, 23 – 25 | `llama-3.1-8b-instant` |
| 26 (optional live cell) | `llama-3.1-8b-instant` — the rest of the notebook runs offline |
| 27 – 28 | No model call. Tutorial 28 uses a local decision model |
| 04 (agents), 05 (research) | `qwen/qwen3-32b` |
| 22 (deep agents) | `qwen/qwen3-32b` |

Both models are available on the **free Groq tier**. Switch to any other Groq model by changing the `model_name` in the setup cell of any notebook.

---

## Useful resources

### Official documentation
- [LangChain docs](https://python.langchain.com/) · [LangGraph docs](https://langchain-ai.github.io/langgraph/) · [Groq docs](https://console.groq.com/docs)

### Community & inspiration
- [langchain-ai/langchain](https://github.com/langchain-ai/langchain) — LangChain source
- [langchain-ai/langgraph](https://github.com/langchain-ai/langgraph) — LangGraph source
- [NirDiamant/GenAI_Agents](https://github.com/NirDiamant/GenAI_Agents) — agent patterns collection
- [kyrolabs/awesome-langchain](https://github.com/kyrolabs/awesome-langchain) — curated resource list

---

<div align="center">

<a href="https://groq.com" target="_blank" rel="noopener noreferrer">
  <img
    src="https://console.groq.com/powered-by-groq-dark.svg"
    alt="Powered by Groq for fast inference."
    width="180"
  />
</a>

*Built with ❤️ using LangChain, LangGraph, and Groq*

</div>
