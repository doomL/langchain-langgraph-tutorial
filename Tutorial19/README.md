# Tutorial 19: Long-term Memory and Checkpointing in LangGraph

Welcome to Tutorial 19. LangGraph provides two complementary memory systems: per-thread short-term memory (managed by the checkpointer) and cross-thread long-term memory (managed by the `InMemoryStore` / `BaseStore`). Together they give agents the ability to remember context both within a session and across completely separate sessions.

## What you'll learn

1. Memory systems overview
   - Short-term memory: checkpointer + `thread_id`
   - Long-term memory: `InMemoryStore` and `BaseStore`
   - When to use each and how they complement each other

2. Checkpointer backends
   - `MemorySaver` — in-memory, development only
   - `SqliteSaver` — local persistence across restarts
   - How to resume a conversation on the same `thread_id`

3. Cross-thread memory with `InMemoryStore`
   - Writing facts, preferences, and summaries to the store
   - Querying the store from any node in any thread
   - Namespaces for organising stored memories

4. Practical example
   - Chatbot that remembers user preferences across multiple sessions
   - Automatic memory summarisation pattern

## Prerequisites

- Completion of Tutorials 1-18
- Python 3.11+
- Groq API key (https://console.groq.com)

## Getting Started

### 1. Ensure Virtual Environment is Activated

#### Linux/macOS:
```bash
cd langchain-langgraph-tutorial
source venv/bin/activate
cd Tutorial19
```

#### Windows:
```cmd
cd langchain-langgraph-tutorial
.\venv\Scripts\activate
cd Tutorial19
```

### 2. Install Dependencies
```bash
pip install langgraph langchain-groq
```

### 3. Launch Jupyter Notebook
```bash
jupyter notebook Tutorial_19_long_term_memory.ipynb
```

## What's Included

### Core Components
- Tutorial notebook with memory system examples
- Short-term memory with `MemorySaver` and `SqliteSaver`
- Cross-thread `InMemoryStore` integration
- Memory write and retrieval patterns inside nodes

### Key Concepts Covered

#### Checkpointer (Short-term)
- Configuring a graph with `checkpointer=MemorySaver()`
- Passing `{"configurable": {"thread_id": "..."}}` to every invocation
- State persists across multiple `.invoke()` calls on the same thread

#### InMemoryStore (Long-term)
- `store.put(namespace, key, value)` to write a memory
- `store.search(namespace, query)` to retrieve relevant memories
- Injecting the store into nodes via `graph.compile(store=store)`

## Next Steps

After completing this tutorial:
1. Use time travel to inspect historical state (Tutorial 20)
2. Combine long-term memory with the Functional API (Tutorial 21)
3. Feed stored memories into a Deep Agent (Tutorial 22)

## Additional Resources
- [LangGraph Memory Concepts](https://langchain-ai.github.io/langgraph/concepts/memory/)
- [LangGraph Persistence How-To](https://langchain-ai.github.io/langgraph/how-tos/persistence/)
- [Groq API Documentation](https://console.groq.com/docs/openai)
