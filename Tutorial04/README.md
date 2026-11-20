# Tutorial 4: Agents in LangChain

Welcome to the fourth tutorial in our LangChain and LangGraph series! In this tutorial, we'll explore the concept of Agents in LangChain, which are autonomous entities capable of using tools and making decisions to accomplish tasks.

> **November 2026.** `create_react_agent` is deprecated. The notebook uses `create_agent` from `langchain.agents`, and `system_prompt=` instead of `prompt=`. The old factory still imports, but it warns and is on the way out. See the [root README](../README.md#new-version-update-november-2026).

## What you'll learn

1. Understanding the agent architecture in LangChain
2. Exploring different types of agents:
   - Zero-shot React Agent
   - Conversational Agent
   - Plan-and-Execute Agent
3. Creating custom tools for agents
4. Implementing a multi-tool agent for task solving

## Prerequisites

- Completion of Tutorials 1-3
- Familiarity with Python and Jupyter Notebooks
- A Groq API key (sign up at https://console.groq.com)

## Getting Started

### 1. Ensure Virtual Environment is Activated

#### For Linux/macOS:
```bash
cd langchain-langgraph-tutorial
source venv/bin/activate
cd Tutorial04
```

#### For Windows:
```cmd
cd langchain-langgraph-tutorial
.\venv\Scripts\activate
cd Tutorial04
```

### 2. Launch Jupyter Notebook
```bash
jupyter notebook Tutorial_4_Agents_in_LangChain.ipynb
```

## What's Included

### Core Components
- `Tutorial_4_Agents_in_LangChain.ipynb`: Main tutorial notebook
- `tools/`: Custom tool implementations
- `examples/`: Sample agent configurations
- `README.md`: Documentation file

### Key Topics

#### Agent Types
- Zero-shot React Agent
  - Dynamic tool selection
  - Reasoning process
  - Output formatting
- Conversational Agent
  - Memory management
  - Context handling
  - Response generation
- Plan-and-Execute Agent
  - Task decomposition
  - Step sequencing
  - Progress monitoring

#### Custom Tools
- Tool creation framework
- Input/output schemas
- Error handling
- Rate limiting

## Troubleshooting

### Common Issues

1. **Agent Execution Problems**
   - Tool availability checks
   - Input validation
   - Memory constraints
   - Response parsing

2. **Performance Optimization**
   - Tool selection efficiency
   - Memory management
   - Response caching
   - Error recovery

## Next Steps

After completing this tutorial:
1. Build custom agent architectures
2. Develop specialized tools
3. Implement complex workflows
4. Prepare for Tutorial 5: Advanced Agent Techniques

Stay tuned for Tutorial 5 where we'll explore:
- Multi-agent systems
- Agent orchestration
- Complex decision trees
- Advanced tool integration

## Additional Resources

- LangChain Agents Documentation
- Tool Development Guide
- Agent Architecture Patterns
- Performance Optimization Tips

Happy learning!