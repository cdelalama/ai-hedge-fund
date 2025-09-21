# Agent Reference

This document summarizes the personas and tooling agents that collaborate inside the AI Hedge Fund workflow. Use it to understand each node's responsibilities and expected outputs.

## Analyst Personas

| Agent | Focus | Key Signals |
|-------|-------|-------------|
| Aswath Damodaran | Story-driven valuation discipline | Revenue narrative alignment, intrinsic value estimates |
| Ben Graham | Deep value with margin of safety | Balance-sheet health, undervaluation thresholds |
| Bill Ackman | Activist catalyst hunts | Turnaround potential, management actions |
| Cathie Wood | Innovation-led growth | Disruption thesis, market expansion forecasts |
| Charlie Munger | Quality franchises | Moat durability, management quality |
| Michael Burry | Contrarian deep value | Hidden risks, asymmetric bets |
| Mohnish Pabrai | Low-risk doubles | Downside protection, upside catalysts |
| Peter Lynch | Everyday ten-baggers | Consumer trends, scalable narratives |
| Phil Fisher | Scuttlebutt-style growth | R&D intensity, competitive advantages |
| Rakesh Jhunjhunwala | Emerging market conviction | Macro tailwinds, India-specific dynamics |
| Stanley Druckenmiller | Macro opportunities | Liquidity cycles, global growth regimes |
| Warren Buffett | Wonderful companies at fair prices | Return on capital, durable cash flows |

## Core System Agents

- **Valuation Agent** – Consolidates analyst valuation metrics and builds intrinsic value ranges used by downstream nodes.
- **Sentiment Agent** – Aggregates news, social, and alternative data sentiment indicators.
- **Fundamentals Agent** – Scrubs financial statements and factor models for company health checks.
- **Technicals Agent** – Computes technical indicators and momentum signals from historical prices.
- **Risk Manager (`src/agents/risk_manager.py`)** – Enforces position sizing, leverage, and drawdown policies; consumes analyst and tooling signals.
- **Portfolio Manager (`src/agents/portfolio_manager.py`)** – Produces the simulated order book, combining investment theses with risk constraints.

## Data & Tooling Interfaces

- **Data Fetchers (`src/data/`)** – Fetch price history, fundamentals, and alternative data from configured providers.
- **LLM model registry (`src/llm/models.py`)** – Wrap OpenAI, Groq, Anthropic, DeepSeek, or local models exposed through Ollama.
- **Tool Registry (`src/tools/`)** – Houses helper utilities (calculators, vector searches, etc.) that agents can call during reasoning.

## Workflow Expectations

- Each analyst persona returns a structured JSON payload with confidence scores, thesis rationale, and recommended positioning bias.
- Tooling agents enrich the shared `AgentState` with computed indicators.
- The Risk Manager validates the combined response and can veto or cap exposures.
- The Portfolio Manager is the only node allowed to emit the final trading decision.

## Extending the System

When adding a new agent:

1. Define the persona or tool under the appropriate module (`src/agents/` or `src/tools/`).
2. Register the node in `src/utils/analysts.py` or the relevant workflow factory.
3. Update tests to cover the new logic.
4. Document the addition in docs/llm/HANDOFF.md and append to docs/llm/HISTORY.md.

Keeping this reference updated ensures contributors understand how reasoning responsibilities are partitioned.




