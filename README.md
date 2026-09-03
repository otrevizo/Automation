# Automation

**Owner:** Oscar Trevizo
**Status:** Early stage — repo scaffolded September 2026, first real n8n use case in progress

My data science foundation comes from continuing education at Harvard University (Graduate Data Science Program, Harvard Extension School and Professional Studies) — this project is a natural extension of that base into a new domain: automation and workflow tooling.

## Purpose

This repo holds the actual automation workflows I build — starting with [n8n](https://n8n.io/), and possibly expanding to other automation tools later. It covers:

- Teaching examples for my AI in Industry university course, which covers n8n at a high level
- Automation experiments and use cases
- Use cases discovered while researching n8n (including things found on GitHub)

## How this relates to my other repos

- **[Python](https://github.com/otrevizo/Python)** — my Python coding portfolio: vignettes, use cases, toolbox, and datasets. Reusable Python logic (e.g. forecasting code, data wrangling) lives there, not here.
- **Automation (this repo)** — the automation/orchestration side: n8n workflow exports, Docker Compose setup, and docs for wiring automation tools together. Where a workflow here calls out to Python, this repo holds the thin wrapper/integration layer; the underlying Python logic stays in `Python`.

The underlying Mac/Docker/n8n installation (security decisions, install history, pre-install checklist) is tracked separately in a personal "Home Computers Management" project and isn't duplicated here.

## Environment

n8n runs locally via Docker, not exposed outside the machine. Start/stop is explicit for now (not always-on). Setup and security specifics are kept in a private doc, outside this repo.

See `docker/` for the (secrets-free) Compose setup once it's added.

## Repository structure

```
Automation/
├── README.md
├── LICENSE
├── CLAUDE.md          — context for Claude Code when working in this repo
├── workflows/          — exported n8n workflow JSON, one per use case
└── docker/             — secrets-free docker-compose.yml and env template
```

## First use case (in progress)

A finance/stock forecasting workflow for my AI in Industry course — a show-and-tell example, building on an existing ARIMA forecasting notebook (SPY via yfinance, STL decomposition, `pmdarima.auto_arima`) from the `Python` repo.

## License

MIT — see [LICENSE](LICENSE).
