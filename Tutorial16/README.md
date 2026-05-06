# Tutorial 16: Swarm Agents with LangGraph

Welcome to Tutorial 16. We explore the Swarm pattern — a decentralised multi-agent architecture where agents hand off control directly to each other without a central coordinator, using the official `langgraph-swarm` package.

## What you'll learn

1. Swarm pattern fundamentals
   - Peer-to-peer handoffs vs. supervisor-driven routing
   - When to use Swarm instead of Supervisor
   - Active-agent tracking and context isolation

2. Using `langgraph-swarm`
   - `create_swarm()` API
   - Defining handoff tools between agents
   - Separate message histories per agent

3. Practical use cases
   - Customer support with specialist agents
   - Routing based on expertise rather than a central brain
   - Privacy isolation between agents

## Prerequisites

- Completion of Tutorials 1-15
- Python 3.11+
- Groq API key (https://console.groq.com)

## Getting Started

### 1. Ensure Virtual Environment is Activated

#### Linux/macOS:
```bash
cd langchain-langgraph-tutorial
source venv/bin/activate
cd Tutorial16
```

#### Windows:
```cmd
cd langchain-langgraph-tutorial
.\venv\Scripts\activate
cd Tutorial16
```

### 2. Install Dependencies
```bash
pip install langgraph langgraph-swarm langchain-groq
```

### 3. Launch Jupyter Notebook
```bash
jupyter notebook Tutorial_16_swarm_agents.ipynb
```

## What's Included

### Core Components
- Tutorial notebook with practical examples
- Customer support swarm with billing, technical, and general agents
- Handoff tool definitions
- Comparison with the Supervisor pattern

### Key Concepts Covered

#### Swarm Architecture
- `create_swarm(agents, default_active_agent)` factory function
- `create_handoff_tool(agent_name, description)` for peer routing
- How the runtime tracks which agent is currently active

#### When to Use Swarm vs Supervisor
- Swarm: routing logic is distributed, agents know their own boundaries
- Supervisor: one LLM needs full context to make routing decisions

## Next Steps

After completing this tutorial:
1. Embed a swarm as a subgraph inside a larger workflow (Tutorial 17)
2. Add long-term memory so agents remember cross-session context (Tutorial 19)
3. Combine with Deep Agents for complex parallel tasks (Tutorial 22)

## Additional Resources
- [langgraph-swarm GitHub](https://github.com/langchain-ai/langgraph-swarm-py)
- [LangGraph Multi-Agent Concepts](https://langchain-ai.github.io/langgraph/concepts/multi_agent/)
- [Groq API Documentation](https://console.groq.com/docs/openai)
