# CLAUDE.md

Context for Claude Code (or any AI assistant) working in this repo. This repo is the automation/orchestration side of Oscar's work — see `README.md` for the full picture. This file is the local mirror of context tracked in a Cowork project called "Automation" (planning docs live outside this repo, in a `Documents/Claude/Projects/Automation` folder) — if you're picking this up fresh, treat this file as the source of truth for the repo itself.

## Background

Oscar's data science foundation comes from continuing education at Harvard University (Graduate Data Science Program, Harvard Extension School and Professional Studies). This repo is a natural extension of that base into automation/workflow tooling — reference "Harvard University" generally; use "Harvard Extension School" specifically only when naming the program itself.

## What this repo is for

- n8n workflow exports and the Docker Compose setup that runs them
- Teaching examples for my AI in Industry university course
- Automation experiments and use cases
- Possibly other automation tools beyond n8n, later

## What this repo is *not* for

- General Python vignettes/toolbox code — that stays in the separate `Python` repo (`github.com/otrevizo/Python`)
- Mac hardware/software/Docker install history and security rationale — tracked separately, not duplicated here

## Environment

- n8n runs locally via Docker, not exposed outside the machine
- Start/stop is explicit for now (not always-on); revisit only if a real use case needs always-on
- n8n container reaches the host's Python environment (a `myenv` venv it can't see directly) via Docker's `host.docker.internal`
- Setup and security specifics (ports, credentials handling, etc.) are kept in a private planning doc, outside this repo

## Roadmap

1. **Phase 1 (done):** verify the environment persists across restarts
2. **Phase 2:** wire in a yfinance-based data source as an n8n trigger, via a small local HTTP wrapper the n8n container reaches through `host.docker.internal`
3. **Phase 3:** replace a toy decision step with real ARIMA/VAR forecasting logic — the `Python` repo's `use_cases/markets_fcst_ts_arima.ipynb` (SPY via yfinance, STL decomposition, `pmdarima.auto_arima`, 100-day forecast) is the reference starting point
4. **Phase 4:** action step — log results to SQLite via SQLAlchemy, or generate a chart/HTML page

## First real use case

A finance/stock forecasting workflow, built as a show-and-tell example for my AI in Industry course (richer than the simple in-VM exercise students already do). Combines Phase 2 and Phase 3 above.

## Conventions

Any Python code in this repo (wrapper scripts, glue code) should follow Oscar's usual conventions: thorough documentation (docstrings + markdown where relevant), descriptive snake_case names for variables/objects, PascalCase for classes, one-argument-per-line formatting once a function signature gets long (~5+ args). Install libraries only when needed, not preemptively.

## Working style

Plan/discuss first, then execute — step by step, no rushing. Ask before assuming scope on anything ambiguous.
