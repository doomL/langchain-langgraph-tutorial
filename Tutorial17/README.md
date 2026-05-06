# Tutorial 17: Subgraphs in LangGraph

Welcome to Tutorial 17. Subgraphs allow you to embed a compiled LangGraph graph as a single node inside a parent graph. This enables modular, reusable agent logic and clean separation of concerns in complex workflows.

## What you'll learn

1. Subgraph fundamentals
   - What a subgraph is and why it is useful
   - How parent and child graphs share (or isolate) state
   - Checkpointing behaviour in nested graphs

2. Building subgraphs
   - Compiling a child graph and adding it as a node
   - Shared state keys vs. private state keys
   - Navigating from a subgraph back to the parent with `Command(graph=Command.PARENT)`

3. Practical patterns
   - Document processing pipeline as a reusable subgraph
   - Multi-stage research workflow with nested graphs
   - Error handling and fallback across graph boundaries

## Prerequisites

- Completion of Tutorials 1-16
- Python 3.11+
- Groq API key (https://console.groq.com)

## Getting Started

### 1. Ensure Virtual Environment is Activated

#### Linux/macOS:
```bash
cd langchain-langgraph-tutorial
source venv/bin/activate
cd Tutorial17
```

#### Windows:
```cmd
cd langchain-langgraph-tutorial
.\venv\Scripts\activate
cd Tutorial17
```

### 2. Install Dependencies
```bash
pip install langgraph langchain-groq
```

### 3. Launch Jupyter Notebook
```bash
jupyter notebook Tutorial_17_subgraphs.ipynb
```

## What's Included

### Core Components
- Tutorial notebook with layered examples
- Simple subgraph embedding example
- State sharing and isolation patterns
- `Command(graph=Command.PARENT)` navigation

### Key Concepts Covered

#### Subgraph Embedding
- `workflow.add_node("subgraph_node", compiled_child_graph)`
- Automatic state schema merging for shared keys
- Independent checkpointing per subgraph level

#### Command Navigation
- `Command(goto="next_node", graph=Command.PARENT)` to exit a subgraph
- Combining `goto` with state `update` in a single return

## Next Steps

After completing this tutorial:
1. Build a map-reduce workflow that fans out to subgraphs (Tutorial 18)
2. Combine subgraphs with long-term memory (Tutorial 19)
3. Rewrite the same pattern with the Functional API (Tutorial 21)

## Additional Resources
- [LangGraph Subgraphs How-To](https://langchain-ai.github.io/langgraph/how-tos/subgraph/)
- [LangGraph Command Reference](https://langchain-ai.github.io/langgraph/reference/graphs/)
- [Groq API Documentation](https://console.groq.com/docs/openai)
