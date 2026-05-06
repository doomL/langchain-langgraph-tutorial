# Tutorial 18: Parallelization and Map-Reduce with LangGraph

Welcome to Tutorial 18. LangGraph's superstep execution model gives you parallelism for free. This tutorial covers every form of concurrent execution from static fan-out to dynamic Map-Reduce and conditional multi-branch fan-out.

## What you'll learn

1. Parallelization fundamentals
   - How LangGraph's superstep model executes nodes concurrently
   - Fan-out (one → many) and fan-in (many → one) patterns
   - `Annotated` reducers — required when parallel nodes write the same key

2. `Send` API — dynamic Map-Reduce
   - `Send(node_name, state)` for runtime-determined parallelism
   - Map step: distribute items to per-item worker nodes
   - Reduce step: aggregate all worker outputs in one node

3. Conditional fan-out
   - Routing function returning a **list** of node names
   - All listed nodes run in the same superstep (true parallel conditional branches)

4. Stable sorting of parallel outputs
   - Custom `reduce_fanouts` reducer to accumulate `{value, score}` objects
   - Sink node sorts by score for deterministic ordering regardless of arrival order

## Prerequisites

- Completion of Tutorials 1–17
- Groq API key — see [root README](../README.md) for setup instructions
