# Courses

Labs, notes and exercises for AI agent frameworks and tools.

## Structure

| Folder             | Topic / stack                                      |
|--------------------|----------------------------------------------------|
| `01_foundations/`  | OpenAI API basics, labs 01–04, `twin/` Gradio app  |
| `02_openai/`       | OpenAI Agents SDK, `deep_research/` Gradio app    |
| `03_crew/`         | CrewAI — see [coursework/README.md](03_crew/coursework/README.md) |
| `04_langgraph/`    | LangGraph                                         |
| `05_autogen/`      | AutoGen                                           |
| `06_mcp/`          | Model Context Protocol (MCP)                       |
| `assets/`          | Shared assets (images, samples, etc.)             |

Notebooks use `python-dotenv` for `OPENAI_API_KEY` and other secrets. Ensure `.env` is configured in the repo root.

See the [root README](../README.md#first-time-setup) for installation and how to run the notebooks.

`01_foundations/twin/` holds `linkedin.pdf` and `summary.txt`, used by labs 03–04 and by the Twin app. Update them to change the profile.

`02_openai/deep_research/` is a Gradio UI (`app.py`) for a plan → search → write → email pipeline. Launch and env vars: [deep_research/README.md](02_openai/deep_research/README.md). Open http://127.0.0.1:7860.

`03_crew/coursework/` holds standalone CrewAI projects (`debate`, `researcher`, `financial_researcher`). They are not installed by the root `uv sync`. Install, Serper, and `crewai run`: [coursework/README.md](03_crew/coursework/README.md).
