# Tutorial 24: Agent Middleware in LangChain 1.0

Welcome to Tutorial 24. LangChain 1.0 (September 2025) introduced a middleware system for `create_agent()` that lets you inject logic at any point in the agent loop — before the model call, after it, or to modify the request itself. Middleware is the foundation of "context engineering": controlling what the model sees and when.

## What you'll learn

1. Middleware fundamentals
   - What middleware is and where it fits in the agent loop
   - The three hook points: `before_model`, `after_model`, `wrap_model_call`
   - How middleware composes with `create_agent()`

2. Built-in middleware
   - HITL middleware — pause before tool execution for human approval
   - Summarisation middleware — auto-summarise long message histories
   - Prompt caching middleware — add cache control headers automatically

3. Custom middleware
   - Writing a logging middleware
   - Writing a guardrail middleware that validates LLM output
   - `wrap_model_call(request, handler)` — wrapping the actual API call
   - Chaining multiple middleware together

4. Context engineering patterns
   - Preventing context pollution across agent steps
   - Context quarantine for sensitive data
   - Dynamic system prompt injection via `modify_model_request`

## Prerequisites

- Completion of Tutorials 1-23
- Python 3.11+
- Groq API key (https://console.groq.com)

## Getting Started

### 1. Ensure Virtual Environment is Activated

#### Linux/macOS:
```bash
cd langchain-langgraph-tutorial
source venv/bin/activate
cd Tutorial24
```

#### Windows:
```cmd
cd langchain-langgraph-tutorial
.\venv\Scripts\activate
cd Tutorial24
```

### 2. Install Dependencies
```bash
pip install langchain langchain-groq langgraph
```

### 3. Launch Jupyter Notebook
```bash
jupyter notebook Tutorial_24_agent_middleware.ipynb
```

## What's Included

### Core Components
- Tutorial notebook with middleware examples
- Logging middleware implementation
- Guardrail middleware with output validation
- HITL middleware integration
- Context-window summarisation middleware

### Key Concepts Covered

#### Hook Points
| Hook | When it runs | Use cases |
|---|---|---|
| `before_model` | Before every LLM call | Logging, routing, state checks |
| `after_model` | After every LLM call | Validation, HITL, guardrails |
| `modify_model_request` | Just before the API call | Edit tools, prompt, message list |

#### create_agent()
- `create_agent(model, tools, middleware=[...])` — new LangChain 1.0 API
- Replaces `AgentExecutor` and `create_react_agent` from older versions
- Returns a standard LangGraph runnable

## Next Steps

After completing this tutorial:
1. Apply middleware to a Deep Agent (Tutorial 22)
2. Combine HITL middleware with the interrupt() primitive (Tutorial 14)
3. Extend middleware to support MCP tool protocols (Tutorial 25)

## Additional Resources
- [LangChain Agent Middleware Blog Post](https://www.langchain.com/blog/agent-middleware)
- [LangChain 1.0 Release Notes](https://blog.langchain.com/langchain-langgraph-1dot0/)
- [Groq API Documentation](https://console.groq.com/docs/openai)
