# Tutorial 21: Functional API in LangGraph

Welcome to Tutorial 21. LangGraph's Functional API is an alternative to `StateGraph` that lets you write workflows as plain Python functions using two decorators: `@entrypoint` and `@task`. It is simpler for sequential and iterative patterns, shares the same underlying runtime, and supports all LangGraph features including HITL, streaming, and cross-thread memory.

## What you'll learn

1. Functional API fundamentals
   - `@entrypoint` — defines the workflow entry point and manages checkpointing
   - `@task` — defines a discrete unit of work that returns a future
   - How both decorators share the same LangGraph runtime as `StateGraph`

2. Key features
   - `previous` parameter — retrieve the last return value on the same thread
   - `store` parameter — inject the cross-thread memory store
   - `interrupt()` — pause execution and wait for human input (same API as StateGraph)
   - `StreamWriter` — emit custom streaming events

3. When to use Functional API vs StateGraph
   - Functional API: simpler sequential and iterative logic, no explicit edges
   - StateGraph: finer-grained checkpointing, visual graph representation, parallel branches
   - Mixing both: a `@task` can call a compiled `StateGraph` and vice-versa

## Prerequisites

- Completion of Tutorials 1-20
- Python 3.11+
- Groq API key (https://console.groq.com)

## Getting Started

### 1. Ensure Virtual Environment is Activated

#### Linux/macOS:
```bash
cd langchain-langgraph-tutorial
source venv/bin/activate
cd Tutorial21
```

#### Windows:
```cmd
cd langchain-langgraph-tutorial
.\venv\Scripts\activate
cd Tutorial21
```

### 2. Install Dependencies
```bash
pip install langgraph langchain-groq
```

### 3. Launch Jupyter Notebook
```bash
jupyter notebook Tutorial_21_functional_api.ipynb
```

## What's Included

### Core Components
- Tutorial notebook with `@entrypoint` and `@task` examples
- Same workflow implemented in both StateGraph and Functional API for comparison
- HITL pattern using `interrupt()` inside a functional workflow
- Cross-thread memory with `previous` and `store`

### Key Concepts Covered

#### @entrypoint
- Single input parameter, returns the final result
- Automatically manages checkpointing with a configured `checkpointer`
- `previous` parameter gives access to the last returned value on the same thread

#### @task
- Returns a `LangGraphTask` future
- Results are persisted: completed tasks are not re-run on resume after interrupt
- Can be called with standard `await` or `.result()` in sync contexts

## Next Steps

After completing this tutorial:
1. Use the Functional API to build a Deep Agent (Tutorial 22)
2. Combine `@task` with map-reduce patterns (Tutorial 18)
3. Add Agent Middleware to control execution flow (Tutorial 24)

## Additional Resources
- [LangGraph Functional API Concepts](https://langchain-ai.github.io/langgraph/concepts/functional_api/)
- [LangGraph Functional API How-To](https://langchain-ai.github.io/langgraph/how-tos/use-functional-api/)
- [Groq API Documentation](https://console.groq.com/docs/openai)
