# LLM Handoff - AI Hedge Fund

- **Last Updated:** 2025-09-21 - ChatGPT
- **Context:** Documentation framework established and README aligned with the new structure

## Current Focus

1. Document runtime guidance comparing CLI and web application flows, including shared environment variables.
2. Define testing strategy for `risk_manager` and `portfolio_manager` modules (unit and integration coverage).
3. Evaluate whether the project needs a dedicated changelog or if GitHub Releases are sufficient.

## Status Summary

- DONE: Documentation scaffold created (`LLM_START_HERE.md`, docs/, docs/llm/).
- DONE: README updated with documentation map and repaired anchors/headings.
- DONE: Analyst ordering and related documentation/env updates synchronized.
- DONE: Local dev tooling confirmed (Poetry 2.2.1 installed, dependencies bootstrapped; Node 19.6.0 triggers Vite warning to upgrade to >=20).
- TODO: Workflow-specific documentation still outstanding.
- TODO: Testing guidance for critical agents not yet documented.

## Next Steps

- Draft a runtime guide covering CLI vs web usage (consider `docs/RUNTIME_GUIDE.md`).
- Audit existing tests and outline coverage gaps for risk and portfolio agents.
- Decide on the changelog approach and document the decision.

## Blockers

- None at this time.

## Open Questions

- Should we add a dedicated changelog file or rely on GitHub Releases?
- Do we need Docker-specific docs for deploying the web app in production?

Keep this handoff under two screens and update it at the end of every working session.
