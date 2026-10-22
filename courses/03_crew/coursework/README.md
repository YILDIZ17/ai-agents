# CrewAI

[CrewAI](https://docs.crewai.com) runs several agents on a shared job. Each agent has a role, a goal, a backstory, and an LLM. Tasks run one after another (`Process.sequential`).

These labs are **not** part of the repo-root environment. `uv sync` at the root of `ai-agents/` does not install CrewAI. Each project here has its own `pyproject.toml` and its own `.venv`.

## Install

**1. CLI, once per machine:**

```powershell
uv tool install crewai
uv tool list
```

**2. Dependencies of one project** — from that project's folder:

```powershell
crewai install
```

That syncs `crewai[tools]` (Python `>=3.10,<3.14`).

## API keys

Put these in the repo-root `.env` (git-ignored). CrewAI loads it when you run from a project folder.

| Variable | Required for | Where to get it |
|----------|----------------|-----------------|
| `OPENAI_API_KEY` | Every project | [platform.openai.com](https://platform.openai.com) |
| `SERPER_API_KEY` | Any agent that uses `SerperDevTool` (web search) | [serper.dev](https://serper.dev) — free tier, no card needed for the starter quota |

`financial_researcher` searches the web, so both keys are required there. `debate` and `researcher` only need OpenAI.

## Run a project

From the project folder (not the repo root):

```powershell
cd courses/03_crew/coursework/financial_researcher
crewai run
```

Stop a run with **Ctrl + C**. All three use `openai/gpt-5.4-mini`, set on each agent in `src/<name>/config/agents.yaml`.

| Project | What it does | Output |
|---------|----------------|--------|
| `debate/` | Asks for a motion, then argue for, argue against, judge | `output/propose.md`, `output/oppose.md`, `output/decide.md` |
| `researcher/` | Researches the topic set in `src/researcher/main.py` | `report.md` |
| `financial_researcher/` | Asks for a company, searches the web, then writes an analysis | `output/report.md` |

Change the researcher topic in `run()` inside `src/researcher/main.py` (`topic`, `current_year`) before `crewai run`. `debate` and `financial_researcher` ask for the motion or the company in the terminal.

## Tools and context

Two things added on top of the scaffold, both in `financial_researcher`.

**Tool** — give an agent a web search. In `crew.py`, only the researcher gets it (the analyst does not search):

```python
from crewai_tools import SerperDevTool

@agent
def researcher(self) -> Agent:
    return Agent(
        config=self.agents_config['researcher'],
        tools=[SerperDevTool()],
    )
```

`SerperDevTool` reads `SERPER_API_KEY`.

**Context** — pick which earlier tasks a task can see. In `tasks.yaml`, the analysis only receives the research, not every previous message:

```yaml
analysis_task:
  agent: analyst
  context:
    - research_task
  output_file: output/report.md
```

Without `context`, a sequential crew passes every earlier task output. `{company}` and `{current_date}` in the YAML are filled from the dict in `main.py`.

## Where things live

| File | Role |
|------|------|
| `src/<name>/config/agents.yaml` | Role, goal, backstory, model |
| `src/<name>/config/tasks.yaml` | Task text, expected output, agent, `context`, `output_file` |
| `src/<name>/crew.py` | Wires agents, tasks, and tools |
| `src/<name>/main.py` | Inputs passed to `kickoff` (`motion`, `topic`, `company`, …) |

## New project

The type argument is `crew`:

```powershell
cd courses/03_crew/coursework
crewai create crew my_crew
cd my_crew
crewai install
crewai run
```
