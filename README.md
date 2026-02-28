# AI'Agents

Personal repository for AI agents experiments — labs, notes, and real projects.

## Structure

| Folder      | Description                                                                 |
|-------------|-----------------------------------------------------------------------------|
| `courses/`  | Notes, Jupyter notebooks and labs (foundations, OpenAI, CrewAI, LangGraph, AutoGen, MCP) |
| `projects/` | Real agent projects (each in its own subfolder with its own README)         |
| `docs/`     | Higher-level documentation, design notes, and framework comparisons         |

## Setup

- **Python**: 3.12+
- **Package manager**: [uv](https://docs.astral.sh/uv/) (or `pip` via `requirements.txt`)

```bash
# With uv
uv sync

# Or with pip
pip install -r requirements.txt
```

Create a `.env` file for API keys. At minimum:

- `OPENAI_API_KEY` — for OpenAI models

## Stack

- **Frameworks**: OpenAI Agents SDK, LangGraph, CrewAI, AutoGen, Semantic Kernel
- **LLMs**: OpenAI, Anthropic (LangChain integrations)
- **Tools**: MCP, Gradio, Playwright, LangSmith

## Author

- [Tümay YILDIZ](https://github.com/YILDIZ17)
