# Tutorial 9: Combining LangChain and LangGraph

Welcome to Tutorial 9. LangChain and LangGraph are strongest together — LangChain provides the building blocks (tools, chains, prompts), LangGraph provides the stateful execution graph. This tutorial shows three practical integration patterns.

## What you'll learn

1. LangChain tools inside LangGraph nodes
   - Wrapping `Tool` objects and LCEL chains as node functions
   - Passing LangChain chains as graph components
   - Async LCEL with `asyncio.gather` for concurrent LLM calls

2. Optimising with async LCEL
   - `chain.ainvoke()` for non-blocking requests
   - `asyncio.gather()` to run multiple chains concurrently
   - Measuring the speedup vs sequential execution

3. Corrective RAG (CRAG) with LangGraph
   - Self-grading retrieval: grade documents before generating
   - Decision gate: relevant → generate; poor quality → rewrite query → web search → generate
   - Structured output grader with `llm.with_structured_output()`
   - CRAG graph: `retrieve → grade_documents → (transform_query + web_search) OR generate`

## Prerequisites

- Completion of Tutorials 1–8
- Groq API key — see [root README](../README.md) for setup instructions
