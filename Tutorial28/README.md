# Tutorial 28: Decision Models

Welcome to Tutorial 28. LangChain 1.5 adds decision models for typed answers: a probability (`Noul`), a label (`Choice`), a rubric score (`Score`), or a region of an image (`Box`). Model routing and risky-tool blocking are middleware that call a decision model.

> **Added in the November 2026 update.** LangChain 1.5 added the Decisions API and the beta middleware that uses it. The notebook implements a local classifier so the routing and the block are visible without a TypeSafe API key. See the [root README](../README.md#new-version-update-november-2026).

## What you'll learn

1. The Decisions API
   - `BaseDecisionModel`
   - `Noul`, `Choice`, and `Score`
   - Reading `response.nouls`, `response.choices`, and `response.scores`

2. A local classifier
   - Subclass `BaseDecisionModel` and implement `_classify`
   - The notebook's keyword model needs no API key
   - `TypeSafeClassifier` is the hosted classifier and needs `TYPESAFE_API_KEY`

3. Middleware
   - `ModelRouterMiddleware` picks the model for a whole run
   - `AutoModeMiddleware` blocks a named tool when the risk probability is at least 0.5
   - Both are beta and require `classifier=`

## Prerequisites

- Completion of Tutorials 1–27, especially Tutorial 24
- Python 3.11+
- No API key for the notebook as written

## Getting Started

```bash
cd langchain-langgraph-tutorial
source .venv/bin/activate
cd Tutorial28
jupyter notebook Tutorial_28_decision_models.ipynb
```

## Additional Resources

- [Prebuilt middleware](https://docs.langchain.com/oss/python/langchain/middleware/built-in)
- [TypeSafe integration](https://docs.langchain.com/oss/python/integrations/providers/typesafe)
