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

### First-time setup

Run all commands from the repo root.

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

**2. Install dependencies** (creates `.venv/` from `pyproject.toml` + `uv.lock`)

```bash
uv sync
```

Or with pip: `pip install -r requirements.txt`.

**3. Create a `.env` file** at the repo root (it is git-ignored):

```env
OPENAI_API_KEY=sk-...
# Optional
ANTHROPIC_API_KEY=...
PUSHOVER_USER=...    # push notifications (lab 04 / twin)
PUSHOVER_TOKEN=...
```

**4. (Optional) Install Playwright browsers**, only needed for browser-based labs:

```bash
uv run playwright install
```

### Running the notebooks

**Option A — in Cursor / VS Code**

1. Open a `.ipynb` file (e.g. `courses/01_foundations/01_lab01.ipynb`).
2. Click **Select Kernel** (top right) → **Python Environments** → `.venv` (Python 3.12).
3. Run cells with **Shift + Enter**.

**Option B — Jupyter Lab in the browser**

```bash
uv run --with jupyter jupyter lab
```

Stop the server with **Ctrl + C**.

> After a kernel restart, always re-run the cells from the top (imports, `load_dotenv()`, ...) before the others.

### Running a Python script / app

```bash
uv run python path/to/script.py
```

Example — the Digital Twin Gradio app:

```bash
cd courses/01_foundations/twin
uv run app.py
```

Then open the URL shown in the terminal (usually http://127.0.0.1:7860).

### Day-to-day

- After a `git pull` or a change in `pyproject.toml`: `uv sync`
- Add a dependency: `uv add <package>`

## Stack

- **Frameworks**: OpenAI Agents SDK, LangGraph, CrewAI, AutoGen, Semantic Kernel
- **LLMs**: OpenAI, Anthropic (LangChain integrations)
- **Tools**: MCP, Gradio, Playwright, LangSmith

## Author

- [Tümay YILDIZ](https://github.com/YILDIZ17)
