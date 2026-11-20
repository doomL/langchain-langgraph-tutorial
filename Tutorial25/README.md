# Tutorial 25: MCP and A2A Protocol

Welcome to Tutorial 25. This tutorial covers two open standards that define how modern AI agents interact with the world: the **Model Context Protocol (MCP)** for agent-to-tool communication, and the **Agent-to-Agent (A2A) Protocol** for cross-framework agent interoperability. Together they form the interoperability stack for production multi-agent systems.

> **November 2026.** LangChain 1.4 replaced `MultiServerMCPClient` with `MCPAdapter` in `langchain.mcp` (still beta). The notebook talks to an in-process FastMCP server, so it runs without Node.js. A2A is served by the Agent Server (`langgraph dev` exposes `/a2a/{assistant_id}`). There is no `LangGraphServer` class in the `langgraph` package. See the [root README](../README.md#new-version-update-november-2026).

## What you'll learn

1. Model Context Protocol (MCP)
   - What MCP is and why it standardises tool interfaces
   - Running a local MCP server (stdio and SSE transports)
   - Connecting a LangGraph agent to MCP tools with `MCPAdapter`
   - MCP as the "REST API for tools"

2. Agent-to-Agent (A2A) Protocol
   - What A2A is and its relationship to MCP
   - A2A RPC methods: `message/send`, `message/stream`, `tasks/get`
   - Exposing a LangGraph agent as an A2A server
   - Calling an A2A agent from another framework (e.g. CrewAI)

3. Practical integration
   - LangGraph agent consuming MCP filesystem tools
   - Two LangGraph agents communicating via A2A
   - Provider-neutral agent network using both protocols

## Prerequisites

- Completion of Tutorials 1-24
- Python 3.11+
- Groq API key (https://console.groq.com)

## Getting Started

### 1. Ensure Virtual Environment is Activated

#### Linux/macOS:
```bash
cd langchain-langgraph-tutorial
source venv/bin/activate
cd Tutorial25
```

#### Windows:
```cmd
cd langchain-langgraph-tutorial
.\venv\Scripts\activate
cd Tutorial25
```

### 2. Install Dependencies
```bash
pip install "langchain[mcp]" langgraph langchain-groq
```

### 3. Launch Jupyter Notebook
```bash
jupyter notebook Tutorial_25_mcp_a2a_protocol.ipynb
```

## What's Included

### Core Components
- Tutorial notebook with MCP and A2A examples
- Local MCP server setup (filesystem tools)
- LangGraph agent consuming MCP tools via `langchain-mcp-adapters`
- A2A server/client demonstration
- Cross-framework agent call example

### Key Concepts Covered

#### MCP (Model Context Protocol)
- Developed by Anthropic, now an open standard
- Transport options: `stdio` (local process), `SSE` (HTTP server)
- `MCPAdapter` from `langchain.mcp` (beta; replaces `MultiServerMCPClient`)
- Tool discovery and invocation through a standard interface

#### A2A (Agent-to-Agent Protocol)
- Originally developed by Google, donated to Linux Foundation
- Each agent exposes an Agent Card at `/.well-known/agent.json`
- Compatible agents from any framework can interoperate
- LangSmith exposes A2A endpoints at `/a2a/{assistant_id}`

## Next Steps

After completing this tutorial:
1. Stream tokens and tool progress to a UI (Tutorial 26)
2. Build a production multi-agent system combining all patterns
3. Deploy agents with open-source LangGraph Server

## Additional Resources
- [MCP Official Documentation](https://modelcontextprotocol.io/)
- [langchain-mcp-adapters GitHub](https://github.com/langchain-ai/langchain-mcp-adapters)
- [A2A Protocol Specification](https://google.github.io/A2A/)
- [LangGraph A2A Support](https://langchain-ai.github.io/langgraph/)
- [Groq API Documentation](https://console.groq.com/docs/openai)
