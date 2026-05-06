# Tutorial 7: Introduction to LangGraph

Welcome to Tutorial 7. Here we introduce LangGraph — the graph-based execution engine that powers all advanced multi-agent patterns covered in Tutorials 8–25.

## What you'll learn

1. LangGraph fundamentals
   - What LangGraph is and how it differs from LangChain
   - Nodes, edges, and state management
   - Compiling and running a `StateGraph`

2. `add_messages` and `MessagesState`
   - Why a plain `list` field breaks under concurrent updates
   - The `add_messages` reducer — appending without overwriting
   - Defining your own `ChatState(TypedDict)` with `Annotated`

3. `ToolNode` — prebuilt tool execution
   - How `ToolNode` reads `AIMessage.tool_calls` and returns `ToolMessage` results
   - Parallel tool calls in a single model turn
   - Direct tool invocation with the `@tool` decorator

4. Building a ReAct agent from scratch
   - The classic loop: `agent → should_use_tools → tools → agent`
   - `add_conditional_edges` with an explicit `path_map`
   - How `create_react_agent` implements this internally

## Prerequisites

- Completion of Tutorials 1–6
- Groq API key — see [root README](../README.md) for setup instructions
