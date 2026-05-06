# Tutorial 22: Deep Agents

Welcome to Tutorial 22. Deep Agents is the official LangChain abstraction for building agents that go beyond simple tool-calling loops. Announced in July 2025, the `deepagents` package provides the pattern seen in products like Deep Research, Manus, and Claude Code — combining detailed system prompts, a planning tool, sub-agent spawning, and filesystem access.

## What you'll learn

1. Deep Agent architecture
   - Why simple tool-calling agents ("shallow agents") have limits
   - The four pillars: detailed prompt, planning, sub-agents, filesystem
   - How `deepagents` is built on top of LangGraph

2. Using `create_deep_agent()`
   - Minimal setup and provider-agnostic model configuration
   - Built-in tools: `write_todos`, `read_file`, `write_file`, `edit_file`, `task`
   - Adding custom tools on top of the defaults

3. Sub-agent patterns
   - Spawning isolated child agents with the `task` tool
   - Async sub-agents (v0.5+): `start_async_task`, `check_async_task`
   - Context window isolation between parent and child

4. Practical example
   - Deep research agent that plans, delegates, and synthesises a report

## Prerequisites

- Completion of Tutorials 1-21
- Python 3.11+
- Groq API key (https://console.groq.com)

## Getting Started

### 1. Ensure Virtual Environment is Activated

#### Linux/macOS:
```bash
cd langchain-langgraph-tutorial
source venv/bin/activate
cd Tutorial22
```

#### Windows:
```cmd
cd langchain-langgraph-tutorial
.\venv\Scripts\activate
cd Tutorial22
```

### 2. Install Dependencies
```bash
pip install deepagents langchain-groq
```

### 3. Launch Jupyter Notebook
```bash
jupyter notebook Tutorial_22_deep_agents.ipynb
```

## What's Included

### Core Components
- Tutorial notebook with Deep Agent examples
- Minimal `create_deep_agent()` setup
- Custom tool integration
- Sub-agent spawning and result collection
- Deep research workflow demonstration

### Key Concepts Covered

#### create_deep_agent()
- `model` — any LangChain-compatible chat model
- `tools` — list of additional tools beyond the built-in set
- `system_prompt` — detailed instructions with few-shot examples

#### Built-in Tools
| Tool | Purpose |
|---|---|
| `write_todos` | Planning — break tasks into tracked steps |
| `read_file` / `write_file` / `edit_file` | Filesystem operations for memory and output |
| `task` | Spawn a synchronous child agent |
| `start_async_task` | Spawn a non-blocking child agent (v0.5+) |

## Next Steps

After completing this tutorial:
1. Build a domain-specific deep research agent for your use case
2. Combine with long-term memory for persistent agent knowledge (Tutorial 19)
3. Add HITL approval before the agent acts (Tutorial 14)

## Additional Resources
- [deepagents GitHub](https://github.com/langchain-ai/deepagents)
- [Deep Agents Official Docs](https://docs.langchain.com/oss/python/deepagents/overview)
- [Deep Agents Announcement Blog](https://www.langchain.com/blog/deep-agents)
- [Groq API Documentation](https://console.groq.com/docs/openai)
