# Tutorial 20: Time Travel and State Replay in LangGraph

Welcome to Tutorial 20. Because LangGraph checkpoints state after every single node execution, it is possible to retrieve the full execution history of a run and re-invoke the graph from any prior checkpoint. This capability — called Time Travel — is essential for debugging, auditing, and exploring alternative execution paths.

## What you'll learn

1. Time Travel fundamentals
   - Why every node execution produces a checkpoint
   - The concept of a "state snapshot" and its metadata
   - Branching the execution history to explore alternatives

2. Core APIs
   - `graph.get_state_history(config)` — iterate all past checkpoints
   - `graph.get_state(config)` — retrieve the current state
   - `graph.update_state(config, values)` — manually edit state mid-run
   - Re-invoking from a specific checkpoint via `checkpoint_id`

3. Practical use cases
   - Debugging a failed agent run by stepping backwards
   - Forking execution to compare different agent responses
   - Manually correcting agent state before continuing

## Prerequisites

- Completion of Tutorials 1-19
- Python 3.11+
- Groq API key (https://console.groq.com)

## Getting Started

### 1. Ensure Virtual Environment is Activated

#### Linux/macOS:
```bash
cd langchain-langgraph-tutorial
source venv/bin/activate
cd Tutorial20
```

#### Windows:
```cmd
cd langchain-langgraph-tutorial
.\venv\Scripts\activate
cd Tutorial20
```

### 2. Install Dependencies
```bash
pip install langgraph langchain-groq
```

### 3. Launch Jupyter Notebook
```bash
jupyter notebook Tutorial_20_time_travel.ipynb
```

## What's Included

### Core Components
- Tutorial notebook with time travel examples
- Full execution history inspection
- State editing and forking demonstration
- Replay from arbitrary checkpoint

### Key Concepts Covered

#### State History
- `StateSnapshot` objects: `values`, `metadata`, `config`, `next`, `created_at`
- Iterating history with `get_state_history(config)`
- Identifying the right checkpoint to rewind to

#### Forking Execution
- Passing a prior `checkpoint_id` in the config to re-invoke
- Creating divergent branches from the same run
- Comparing outputs of different branches

## Next Steps

After completing this tutorial:
1. Explore the Functional API which shares the same checkpointing model (Tutorial 21)
2. Combine time travel with HITL for interactive debugging (Tutorial 14)
3. Use `SqliteSaver` for persistent history across restarts (Tutorial 19)

## Additional Resources
- [LangGraph Time Travel How-To](https://langchain-ai.github.io/langgraph/how-tos/time-travel/)
- [LangGraph Persistence Concepts](https://langchain-ai.github.io/langgraph/concepts/persistence/)
- [Groq API Documentation](https://console.groq.com/docs/openai)
