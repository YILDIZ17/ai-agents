# Courses

Labs, notes and exercises for AI agent frameworks and tools.

## Structure

| Folder             | Topic / stack                                      |
|--------------------|----------------------------------------------------|
| `01_foundations/`  | OpenAI API basics, labs 01–04, `twin/` Gradio app  |
| `02_openai/`       | OpenAI Agents SDK                                 |
| `03_crew/`         | CrewAI                                            |
| `04_langgraph/`    | LangGraph                                         |
| `05_autogen/`      | AutoGen                                           |
| `06_mcp/`          | Model Context Protocol (MCP)                       |
| `assets/`          | Shared assets (images, samples, etc.)             |

Notebooks use `python-dotenv` for `OPENAI_API_KEY` and other secrets. Ensure `.env` is configured in the repo root.

See the [root README](../README.md#first-time-setup) for installation and how to run the notebooks.

`01_foundations/twin/` holds `linkedin.pdf` and `summary.txt`, used by labs 03–04 and by the Twin app. Update them to change the profile.
