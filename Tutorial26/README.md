# Tutorial 26: Streaming a LangGraph Run

Welcome to Tutorial 26. The earlier tutorials return one final state from `invoke()`. A chat UI needs the run while it is happening: tokens, tool progress, and a way to keep internal model calls off the screen. This tutorial streams one support-desk graph with LangGraph's `version="v2"` stream format.

## What you'll learn

1. Stream modes
   - `updates`, `values`, `messages`, `custom`, `checkpoints`
   - When to use each one
   - Why `version="v2"` gives every chunk the same shape

2. Token streaming
   - `stream_mode="messages"` from a model called with `.invoke()`
   - Filtering tokens by `langgraph_node`
   - The `nostream` tag for internal model calls

3. Custom progress
   - `get_stream_writer()` inside a node and inside a tool
   - Combining `custom` with `updates` and `messages` in one loop

4. Nested graphs
   - Why a subgraph is one opaque update by default
   - `subgraphs=True` when the model lives inside `create_agent()` or any compiled child graph

## Prerequisites

- Completion of Tutorials 1–25
- Python 3.11+
- Groq API key only for the optional last section (https://console.groq.com)

The main examples use `GenericFakeChatModel`, so they run without an API key.

## Getting Started

### 1. Ensure Virtual Environment is Activated

#### Linux/macOS:
```bash
cd langchain-langgraph-tutorial
source .venv/bin/activate
cd Tutorial26
```

#### Windows:
```cmd
cd langchain-langgraph-tutorial
.venv\Scripts\activate
cd Tutorial26
```

### 2. Install Dependencies
```bash
pip install langgraph langchain-core
```

### 3. Launch Jupyter Notebook
```bash
jupyter notebook Tutorial_26_streaming.ipynb
```

## What's Included

### Core Components
- Tutorial notebook with a support-desk graph
- Offline token streaming via `GenericFakeChatModel`
- Custom progress events from a node and a tool
- A terminal renderer that keeps an internal score off screen
- Optional Groq cell, skipped when `GROQ_API_KEY` is unset

### Key Concepts Covered

#### StreamPart (`version="v2"`)
- `type` — which mode produced the chunk
- `ns` — `()` on the root graph, a node path for subgraph events
- `data` — the payload for that mode
- `interrupts` — human-in-the-loop pauses on the same stream

#### Modes used in the notebook
| Mode | Payload |
|---|---|
| `updates` | `{node_name: {keys the node wrote}}` |
| `values` | Full state, starting with the input |
| `messages` | `(message_chunk, metadata)` |
| `custom` | Whatever you passed to `get_stream_writer()` |
| `checkpoints` | A `get_state()` snapshot. Requires a checkpointer |

## Next Steps

After completing this tutorial:
1. Drive the same loop from the FastAPI app in Tutorial 13
2. Surface `part["interrupts"]` with the approval flow in Tutorial 14
3. Stream a Deep Agent (Tutorial 22) — it is a compiled graph

## Additional Resources
- [LangGraph Streaming](https://docs.langchain.com/oss/python/langgraph/streaming)
- [LangGraph Checkpointers](https://docs.langchain.com/oss/python/langgraph/checkpointers)
- [Groq API Documentation](https://console.groq.com/docs/openai)
