# Tutorial 23: LangChain 1.0 Utilities

Welcome to Tutorial 23. LangChain v0.3 and the 1.0 release introduced a set of quality-of-life utilities that simplify model initialisation, message management, and context-window handling. This tutorial covers `init_chat_model()`, `trim_messages()`, `filter_messages()`, and the move to dedicated integration packages.

## What you'll learn

1. Provider-agnostic model initialisation
   - `init_chat_model(model_id)` — initialise any supported model by string identifier
   - Switching providers without changing application code
   - Configurable defaults for temperature, max tokens, etc.

2. Message management utilities
   - `trim_messages()` — fit a message list into a context window budget
   - `filter_messages()` — select messages by role, id, or type
   - `merge_message_runs()` — collapse consecutive same-role messages

3. Dedicated integration packages
   - Why `langchain-openai`, `langchain-anthropic`, `langchain-groq` replaced `langchain-community`
   - How to migrate existing imports
   - Version pinning strategy for integrations

4. Structured output improvements
   - `.with_structured_output(schema)` across all providers
   - JSON mode vs. tool-calling vs. provider-native JSON schema

## Prerequisites

- Completion of Tutorials 1-22
- Python 3.11+
- Groq API key (https://console.groq.com)

## Getting Started

### 1. Ensure Virtual Environment is Activated

#### Linux/macOS:
```bash
cd langchain-langgraph-tutorial
source venv/bin/activate
cd Tutorial23
```

#### Windows:
```cmd
cd langchain-langgraph-tutorial
.\venv\Scripts\activate
cd Tutorial23
```

### 2. Install Dependencies
```bash
pip install langchain langchain-groq langchain-openai
```

### 3. Launch Jupyter Notebook
```bash
jupyter notebook Tutorial_23_langchain_utilities.ipynb
```

## What's Included

### Core Components
- Tutorial notebook with utility examples
- `init_chat_model()` provider switching demo
- Context-window-aware chatbot using `trim_messages()`
- Message filtering and merging patterns
- Structured output with multiple methods

### Key Concepts Covered

#### init_chat_model()
- `init_chat_model("groq:llama-3.3-70b-versatile")` — provider:model format
- Returns a standard `BaseChatModel` compatible with all LangChain components
- Configurable at runtime without code changes

#### trim_messages()
- `max_tokens` — hard limit in tokens
- `strategy` — `"last"` (keep recent) or `"first"` (keep early)
- `token_counter` — plug in any tokeniser
- Preserves system message by default

## Next Steps

After completing this tutorial:
1. Apply these utilities inside Agent Middleware (Tutorial 24)
2. Use `init_chat_model()` in Deep Agents for provider flexibility (Tutorial 22)
3. Build an MCP-compatible agent (Tutorial 25)

## Additional Resources
- [LangChain init_chat_model Docs](https://python.langchain.com/docs/how_to/chat_models_universal_init/)
- [LangChain trim_messages Docs](https://python.langchain.com/docs/how_to/trim_messages/)
- [LangChain v0.3 Migration Guide](https://python.langchain.com/docs/versions/v0_3/)
- [Groq API Documentation](https://console.groq.com/docs/openai)
