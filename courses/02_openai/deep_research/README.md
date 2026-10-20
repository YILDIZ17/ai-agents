# Deep Research

Gradio app that runs a multi-agent web research pipeline (OpenAI Agents SDK): plan searches, search the web, write a markdown report, then send it by email (or as a push notification).

## Launch the UI

All commands are run **from the repo root** (`ai-agents/`). Setup (`uv sync`, `.env`) is in the [root README](../../../README.md#first-time-setup).

```bash
uv run python courses/02_openai/deep_research/app.py
```

Then open **http://127.0.0.1:7860** (the same URL is printed in the terminal). Type a question or pick an example, then click **Investigate**. Stop the server with **Ctrl + C**.

A plain version of the same pipeline, without the custom layout:

```bash
uv run python courses/02_openai/deep_research/simple.py
```

Both use Gradio’s default port `7860`. Run only one at a time.

## What it does

1. **Planner** proposes `HOW_MANY_SEARCHES` web queries (default 5).
2. **Search** agents run those queries in parallel (`WebSearchTool`) and summarize each result.
3. **Writer** turns the summaries into a long markdown report.
4. **Email** agent sends the report. With `USE_EMAIL=false`, it sends a Pushover notification instead.

Status lines stream into the page while the run is in progress, including a link to the OpenAI trace.

## Configuration

`OPENAI_API_KEY` is required in the repo-root `.env`. Everything below is optional.

```env
DEFAULT_MODEL_NAME=gpt-5.4-mini   # model for every agent
HOW_MANY_SEARCHES=5               # searches the planner must output

USE_EMAIL=true                    # false → Pushover instead of SMTP
EMAIL_ADDRESS=you@example.com     # sender and recipient
EMAIL_SMTP_SERVER=smtp.gmail.com
EMAIL_APP_PASSWORD=...

PUSHOVER_USER=...                 # used when USE_EMAIL=false
PUSHOVER_TOKEN=...
```

## Files

| File | Role |
|------|------|
| `app.py` | Styled Gradio UI (the one to launch) |
| `simple.py` | Same pipeline, default Gradio layout |
| `research_manager.py` | Orchestrates plan → search → write → send |
| `planner_agent.py` | Builds the search plan |
| `search_agent.py` | Web search + short summary |
| `writer_agent.py` | Writes the markdown report |
| `email_agent.py` | Sends the report (email or push) |
| `messenger.py` | SMTP and Pushover helpers |
| `styles.py` | CSS, header, and example queries |
