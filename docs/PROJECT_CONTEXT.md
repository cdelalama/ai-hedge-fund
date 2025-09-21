# Project Context

## Purpose

AI Hedge Fund is an experimentation environment that simulates how multiple investment personas and tooling agents can collaborate to produce trading decisions. The project focuses on orchestrating reasoning, valuation, and risk management steps while keeping execution strictly simulated.

## Goals

- Explore agent-based collaboration for equities research and portfolio construction
- Provide both CLI and web entry points for interactive experimentation
- Maintain reproducible backtests for evaluating strategies over historical data
- Offer a safe educational sandbox that never places live trades

## System Architecture

The system is composed of coordinated agents managed through LangGraph workflows.

- **Analyst agents (`src/agents/analysts/`)** gather perspectives such as value, growth, sentiment, and macro analysis. Each agent returns structured signals.
- **Risk Manager (`src/agents/risk_manager.py`)** evaluates aggregated signals, applies guardrails, and sets allowable exposure.
- **Portfolio Manager (`src/agents/portfolio_manager.py`)** consolidates signals and risk limits to output simulated orders.
- **Data layer (`src/data/`)** provides utilities for fetching fundamentals, market data, and sentiment via configured APIs or cached files.
- **LLM tooling (`src/llm/` and `src/tools/`)** wraps provider-specific clients and tools used during reasoning chains.
- **Graph state (`src/graph/`)** defines the shared `AgentState` exchanged between nodes and configures the LangGraph workflow topology.
- **CLI interface (`src/cli/`)** parses user input, orchestrates runs, and exposes flags for reasoning visibility, model selection, and local LLM usage.
- **Backtester (`src/backtester.py`)** replays the workflow on historical intervals, collecting performance metrics for analysis.
- **Web application (`app/`)** provides a FastAPI + frontend surface for running the workflow with richer visualizations.

Supporting assets live under:

- `docker/` – container images and compose files for local or hosted deployments
- `.github/` – CI configurations
- `tests/` – unit and integration coverage for agents, data access, and workflows

## Runtime Modes

1. **Command Line** – Primary engineering and automation interface. Uses Poetry-managed virtual environment and executes `src/main.py`.
2. **Backtesting** – Invokes `src/backtester.py` to evaluate strategies retrospectively. Shares configuration with CLI.
3. **Web Application** – Launches the FastAPI app in `app/` for interactive use. Requires the same environment variables and API keys as the CLI.

## Environment & Secrets

- Python 3.11 is the reference runtime (see `pyproject.toml`).
- Poetry manages dependencies and scripts.
- Secrets (OpenAI, Groq, Anthropic, DeepSeek, financial datasets) must be provided via `.env`. Never commit the `.env` file.
- `.env.example` documents required configuration. Keep it in sync when new variables are introduced.

## Repository Layout (high level)

```
.
├── app/                  # Web application backend/frontend
├── docker/               # Container and deployment assets
├── src/                  # Core workflow, agents, data utilities
├── tests/                # Automated test suites
├── README.md             # High-level project overview and quickstart
├── LLM_START_HERE.md     # Operational entry point for LLM contributors
└── docs/                 # Extended documentation and hand-off notes
```

## Knowledge Sources

- Public financial APIs (via configured providers)
- LLM reasoning through configured models (OpenAI by default, local via Ollama optional)
- Internal dataset caches persisted under `data/` (when implemented)

## Future Considerations

- Align analytics pipelines between CLI and web experiences
- Expand automated testing around portfolio allocation and risk controls
- Formalize evaluation metrics for agent signal quality

Keep docs/llm/HANDOFF.md current with ongoing initiatives and open questions.

