# Tutorial 27: Fault Tolerance in LangGraph

Welcome to Tutorial 27. LangGraph 1.2 can retry a node, cap how long one attempt runs, compensate after the retries are gone, and stop a run between steps without losing its checkpoint.

## What you'll learn

1. Retry policies
   - `RetryPolicy(max_attempts=..., retry_on=...)`
   - Retries happen before an error handler

2. Error handlers
   - `error_handler` receives a `NodeError`
   - Return `Command(update=..., goto=...)` to compensate and continue

3. Timeouts
   - `timeout=` on `add_node` for async nodes
   - `TimeoutPolicy(run_timeout=..., idle_timeout=...)`
   - A timeout is a failed attempt, so retries and the error handler still apply

4. Graceful drain
   - `RunControl.request_drain()`
   - `GraphDrained` after the current superstep
   - Resume with `invoke(None, config)` on the same thread

## Prerequisites

- Completion of Tutorials 1–26
- Python 3.11+
- No API key. Every cell runs locally

## Getting Started

```bash
cd langchain-langgraph-tutorial
source .venv/bin/activate
cd Tutorial27
jupyter notebook Tutorial_27_fault_tolerance.ipynb
```

## Additional Resources

- [Fault tolerance](https://docs.langchain.com/oss/python/langgraph/fault-tolerance)
- [Configure nodes](https://docs.langchain.com/oss/python/langgraph/graph-api-nodes)
