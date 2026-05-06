# Tutorial 1: Introduction to LangChain

Welcome to Tutorial 1 — the starting point of this series. We introduce LangChain, set up the environment, and build your first LLM-powered application.

## What you'll learn

1. What LangChain is and why it exists
2. How to set up the environment and obtain a Groq API key
3. Core concepts: chains, prompts, and output parsers
4. Your first LangChain application with LCEL

## Prerequisites

- Python 3.10 or higher
- Basic Python knowledge
- A free Groq API key — sign up at **[console.groq.com](https://console.groq.com)**

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/DoomL/langchain-langgraph-tutorial.git
cd langchain-langgraph-tutorial
```

### 2. Create and activate a virtual environment

```bash
# Linux / macOS
python3 -m venv .venv
source .venv/bin/activate

# Windows
python -m venv .venv
.venv\Scripts\activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Configure your API key

Create a `.env` file in the repo root:

```plaintext
GROQ_API_KEY=your_groq_api_key_here
```

> **Get your key**: go to [console.groq.com](https://console.groq.com) → *API Keys* → *Create API Key*.

### 5. Open the notebook

```bash
cd Tutorial01
jupyter notebook Tutorial_1_Introduction_to_LangChain.ipynb
```

## Troubleshooting

| Problem | Fix |
|---|---|
| `ModuleNotFoundError` | Make sure the venv is active and `pip install -r requirements.txt` was run |
| `GROQ_API_KEY not set` | Add the key to `.env` and restart the Jupyter kernel |
| Pip install fails | Upgrade pip: `python -m pip install --upgrade pip` |
