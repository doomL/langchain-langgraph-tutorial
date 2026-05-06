# Tutorial 15: Supervisor Agent with LangGraph

Welcome to Tutorial 15. Here we build hierarchical multi-agent systems using the official `langgraph-supervisor` package. A Supervisor is a central LLM that coordinates a team of specialised worker agents, delegating tasks and aggregating results.

## What you'll learn

1. Supervisor pattern fundamentals
   - Central coordinator vs. peer-to-peer patterns
   - How a supervisor routes work through tool calls (handoffs)
   - Worker agent isolation and result aggregation

2. Using `langgraph-supervisor`
   - `create_supervisor()` API
   - `output_mode` options: `"full_history"` vs `"last_message"`
   - Custom handoff tool names and descriptions

3. Multi-level hierarchies
   - Supervisor-of-supervisors pattern
   - Combining with `create_react_agent` workers
   - State sharing between supervisor and workers

## Prerequisites

- Completion of Tutorials 1-14
- Python 3.11+
- Groq API key (https://console.groq.com)

## Getting Started

### 1. Ensure Virtual Environment is Activated

#### Linux/macOS:
```bash
cd langchain-langgraph-tutorial
source venv/bin/activate
cd Tutorial15
```

#### Windows:
```cmd
cd langchain-langgraph-tutorial
.\venv\Scripts\activate
cd Tutorial15
```

### 2. Install Dependencies
```bash
pip install langgraph langgraph-supervisor langchain-groq
```

### 3. Launch Jupyter Notebook
```bash
jupyter notebook Tutorial_15_supervisor_agent.ipynb
```

## What's Included

### Core Components
- Tutorial notebook with step-by-step examples
- Research supervisor with multiple specialised workers
- Custom handoff tool definitions
- Multi-level hierarchy demonstration

### Key Concepts Covered

#### Supervisor Architecture
- `create_supervisor(agents, model, tools, prompt)` factory function
- How workers are exposed as tools to the supervisor LLM
- Conversation flow: user → supervisor → worker → supervisor → user

#### Output Modes
- `full_history`: includes all intermediate worker messages
- `last_message`: returns only the supervisor's final response

## Next Steps

After completing this tutorial:
1. Compare with the Swarm pattern (Tutorial 16)
2. Nest supervisors as subgraphs (Tutorial 17)
3. Add HITL approval before worker execution (Tutorial 14)
4. Scale with async subagents in Deep Agents (Tutorial 22)

## Additional Resources
- [langgraph-supervisor GitHub](https://github.com/langchain-ai/langgraph-supervisor-py)
- [LangGraph Multi-Agent Concepts](https://langchain-ai.github.io/langgraph/concepts/multi_agent/)
- [Groq API Documentation](https://console.groq.com/docs/openai)
