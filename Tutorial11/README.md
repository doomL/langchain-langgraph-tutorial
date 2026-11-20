# Tutorial 11: Working with Structured Data

> **November 2026.** The movie agent uses `create_agent` from `langchain.agents`. `create_react_agent` is deprecated, so new code should not import it. See the [root README](../README.md#new-version-update-november-2026).

## What you'll learn

1. Pydantic Integration:
   - Data validation and modeling
   - Type annotations
   - Schema creation
   - Custom validators

2. Structured I/O:
   - Input validation
   - Output parsing
   - Type safety
   - Error handling

3. JSON Processing:
   - Complex data manipulation
   - Schema validation
   - Data transformation
   - Query operations

4. Application Integration:
   - LangChain components
   - LangGraph workflows
   - Data persistence
   - API development

## Prerequisites

- Completion of Tutorials 1-10
- Python 3.11+
- Groq API key

## Getting Started

### 1. Ensure Virtual Environment is Activated

#### Linux/macOS:
```bash
cd langchain-langgraph-tutorial
source venv/bin/activate
cd Tutorial11
```

#### Windows:
```cmd
cd langchain-langgraph-tutorial
.\venv\Scripts\activate
cd Tutorial11
```

### 2. Launch Jupyter Notebook
```bash
jupyter notebook Tutorial_11_structured_data.ipynb
```

## Components

### Core Files
- `Tutorial_11_structured_data.ipynb`: Main tutorial notebook
- `utils/`: Helper functions
- `examples/`: Sample implementations

### Key Features

#### Data Modeling
- Type validation
- Schema definition
- Model inheritance
- Custom validators

#### Data Processing
- Input parsing
- Output formatting
- Error handling
- Data transformation

#### Integration Tools
- API connectivity
- Database operations
- State management
- Workflow automation

## Next Steps

After completing this tutorial:
1. Build type-safe applications
2. Implement data validation
3. Create structured workflows
4. Develop API integrations

## Additional Resources

- [Pydantic Documentation](https://pydantic-docs.helpmanual.io/)
- [LangChain Documentation](https://python.langchain.com/docs/get_started/introduction.html)
- [LangGraph Documentation](https://python.langchain.com/docs/langgraph)
- [Groq API Documentation](https://www.groq.com/docs/)