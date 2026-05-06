# Tutorial 14: Human-in-the-Loop with LangGraph

Welcome to Tutorial 14. In this tutorial we explore one of the most powerful features of LangGraph: the ability to pause graph execution, wait for human input, and resume exactly where it left off.

## What you'll learn

1. Human-in-the-Loop fundamentals
   - What HITL means in the context of agentic workflows
   - Why pausing and resuming execution is important
   - The difference between the old `NodeInterrupt` and the modern `interrupt()` API

2. Core primitives
   - `interrupt()` — pause inside a node and surface a value to the caller
   - `Command(resume=...)` — resume execution with human-provided data
   - `MemorySaver` — the checkpointer required to persist state between invocations

3. Practical patterns
   - Approval-before-action workflow
   - Human review of agent-generated content
   - Multi-step forms driven by a graph

## Prerequisites

- Completion of Tutorials 1-13
- Python 3.11+
- Groq API key (https://console.groq.com)

## Getting Started

### 1. Ensure Virtual Environment is Activated

#### Linux/macOS:
```bash
cd langchain-langgraph-tutorial
source venv/bin/activate
cd Tutorial14
```

#### Windows:
```cmd
cd langchain-langgraph-tutorial
.\venv\Scripts\activate
cd Tutorial14
```

### 2. Install Dependencies
```bash
pip install langgraph langchain-groq
```

### 3. Launch Jupyter Notebook
```bash
jupyter notebook Tutorial_14_human_in_the_loop.ipynb
```

## What's Included

### Core Components
- Tutorial notebook with practical examples
- Approval workflow implementation
- State persistence with MemorySaver
- Resume patterns with Command

### Key Concepts Covered

#### Interrupt Mechanism
- Calling `interrupt(value)` inside a node
- Surfacing the interrupt value to the outer caller
- Resuming with `Command(resume=user_response)`

#### Checkpointing
- Role of `MemorySaver` (and `SqliteSaver` for persistence across restarts)
- `thread_id` as the identifier for a conversation session
- Re-invoking the same thread to continue execution

## Next Steps

After completing this tutorial:
1. Build multi-day approval workflows
2. Combine HITL with the Supervisor pattern (Tutorial 15)
3. Use HITL inside subgraphs (Tutorial 17)
4. Experiment with the Functional API's `interrupt()` (Tutorial 21)

## Additional Resources
- [LangGraph HITL Concepts](https://langchain-ai.github.io/langgraph/concepts/human_in_the_loop/)
- [LangGraph interrupt() API](https://langchain-ai.github.io/langgraph/reference/graphs/)
- [Groq API Documentation](https://console.groq.com/docs/openai)
