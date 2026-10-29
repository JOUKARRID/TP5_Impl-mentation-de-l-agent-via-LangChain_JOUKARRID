# Agentic AI with LangChain, LangGraph and Ollama

A hands-on notebook exploring AI agents using LangChain, LangGraph, and a
fully local LLM stack powered by Ollama.

## Overview

This project demonstrates how to build an AI agent, define custom tools,
and let the agent select the right tool according to the user's request —
all running locally, with no external API keys required.

## Concepts Covered

- Creating AI agents with LangChain (`create_agent`)
- Defining custom tools with `@tool`
- Tool calling and agent execution loops
- Using locally hosted LLMs via Ollama (`llama3.1`, `qwen2.5:7b`)
- Using local embeddings via Ollama (`nomic-embed-text`)
- Managing conversation state with LangGraph (`InMemorySaver`)
- PostgreSQL checkpointing for persistent conversation memory
- Dynamic model selection (basic vs. advanced) via middleware
- System-prompt control driven by user role
- Structured output with Pydantic (`ToolStrategy`)
- Guardrails: PII detection, Human-in-the-loop, custom content filters
- RAG-as-a-tool with FAISS + retriever tools
- Loading environment variables with `python-dotenv`

## Technologies

- Python 3.11+
- LangChain
- LangGraph
- Ollama (local runtime)
- PostgreSQL
- FAISS (vector store)
- DuckDuckGo Search (`ddgs`) and Tavily
- Jupyter Notebook

## Models Used (all local via Ollama)

| Model              | Role                        | Pull command                       |
| ------------------ | --------------------------- | ---------------------------------- |
| `llama3.1`         | Main chat model (basic)     | `ollama pull llama3.1`             |
| `qwen2.5:7b`       | Advanced / heavier tasks    | `ollama pull qwen2.5:7b`           |
| `nomic-embed-text` | Embeddings for RAG          | `ollama pull nomic-embed-text`     |

## Tools Implemented

- **News search:** Demonstrates a basic news-search tool (demo data).
- **Weather:** Demonstrates a weather-information tool (demo data).
- **Employee information:** Returns sample employee information (demo data).
- **Web search (DuckDuckGo):** Real web search via the `ddgs` package.
- **Web search (Tavily):** Real web search via the Tavily API (requires `TAVILY_API_KEY`).
- **Python REPL:** Executes generated Python code (`PythonREPLTool`).
- **Retriever tool:** Exposes a FAISS vector store as a searchable tool
  (`create_retriever_tool`) for RAG scenarios.

*Note: Search, weather, and employee tools return demonstration data
unless explicitly wired to real data sources.*

## Getting Started

### 1. Clone and set up the environment

```bash
uv init
uv venv
# Windows PowerShell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope Process
.venv\Scripts\activate
# Linux / macOS
source .venv/bin/activate
