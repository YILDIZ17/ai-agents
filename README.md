# AI'Agents

Personal repository for AI agents experiments — labs, notes, and real projects.

## Structure

| Folder      | Description                                                                 |
|-------------|-----------------------------------------------------------------------------|
| `courses/`  | Notes, Jupyter notebooks and labs (foundations, OpenAI, CrewAI, LangGraph, AutoGen, MCP) |
| `projects/` | Real agent projects (each in its own subfolder with its own README)         |
| `docs/`     | Higher-level documentation, design notes, and framework comparisons         |

## Quick start

All commands are run **from the repo root** (`ai-agents/`), in a terminal (PowerShell on Windows).

| I want to...                         | Command                                                  |
|--------------------------------------|----------------------------------------------------------|
| Install / update the environment     | `uv sync`                                                |
| Open the notebooks in the browser    | `uv run jupyter lab`                                     |
| Run a Python script                  | `uv run python path/to/script.py`                        |
| Launch the Digital Twin app          | `uv run python courses/01_foundations/twin/app.py`       |
| Launch the Deep Research UI         | `uv run python courses/02_openai/deep_research/app.py`   |
| Add a dependency                     | `uv add <package>`                                       |
| Stop a running server (Jupyter, app) | **Ctrl + C** in the terminal                             |

No need to activate the virtual environment: `uv run` uses `.venv/` automatically.

## First-time setup

Requirements: **Python 3.12** (pinned in `.python-version`, uv downloads it if missing) and [uv](https://docs.astral.sh/uv/).

**1. Install uv** (once per machine)

```powershell
# Windows (PowerShell)
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

```bash
# macOS / Linux
curl -LsSf https://astral.sh/uv/install.sh | sh
```

Restart the terminal, then check with `uv --version`.

**2. Install dependencies** — creates `.venv/` from `pyproject.toml` + `uv.lock` (includes JupyterLab):

```bash
uv sync
```

Without uv: `pip install -r requirements.txt` (plus `pip install jupyterlab ipykernel` for notebooks).

**3. Create a `.env` file** at the repo root (it is git-ignored):

```env
OPENAI_API_KEY=sk-...
# Optional
ANTHROPIC_API_KEY=...
PUSHOVER_USER=...    # push notifications (lab 04 / twin / deep research)
PUSHOVER_TOKEN=...
SERPER_API_KEY=...   # web search for CrewAI (serper.dev, free tier)
# Deep Research email delivery — see courses/02_openai/deep_research/README.md
# USE_EMAIL=true
# EMAIL_ADDRESS=...
# EMAIL_SMTP_SERVER=smtp.gmail.com
# EMAIL_APP_PASSWORD=...
```

**4. (Optional) Install Playwright browsers**, only needed for browser-based labs:

```bash
uv run playwright install
```

## Running the notebooks

Two ways, pick one.

**Option A — directly in Cursor / VS Code** (nothing to launch)

1. Open a `.ipynb` file (e.g. `courses/01_foundations/01_lab01.ipynb`).
2. Click **Select Kernel** (top right) → **Python Environments** → `.venv` (Python 3.12).
3. Run cells with **Shift + Enter**.

If `.venv` does not show up, run `uv sync` first, then reload the window.

**Option B — JupyterLab in the browser**

```bash
uv run jupyter lab
```

The browser opens automatically (otherwise, open the `http://localhost:8888/lab?token=...` link printed in the terminal). Keep the terminal open while you work; stop the server with **Ctrl + C**.

> After a kernel restart, always re-run the cells from the top (imports, `load_dotenv()`, ...) before the others.

## Running a Python script / app

```bash
uv run python path/to/script.py
```

Example — the Digital Twin Gradio app:

```bash
uv run python courses/01_foundations/twin/app.py
```

Then open http://127.0.0.1:7860 (URL also shown in the terminal). Stop with **Ctrl + C**.

Deep Research (same URL, run only one Gradio app at a time):

```bash
uv run python courses/02_openai/deep_research/app.py
```

See [courses/02_openai/deep_research/README.md](courses/02_openai/deep_research/README.md) for the pipeline and the email / Pushover settings.

## Day-to-day

- After a `git pull` or a change in `pyproject.toml`: `uv sync`
- Add a dependency: `uv add <package>` (dev-only tool: `uv add --dev <package>`)
- Upgrade all dependencies: `uv lock --upgrade` then `uv sync`

## Stack

- **Frameworks**: OpenAI Agents SDK, LangGraph, CrewAI, AutoGen, Semantic Kernel
- **LLMs**: OpenAI, Anthropic (LangChain integrations)
- **Tools**: MCP, Gradio, Playwright, LangSmith

## Author

- [Tümay YILDIZ](https://github.com/YILDIZ17)
