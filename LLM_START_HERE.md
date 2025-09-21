# LLM Start Guide - AI Hedge Fund Project

## READ THIS FIRST (MANDATORY)

You are working on AI Hedge Fund: a proof-of-concept multi-agent system that experiments with AI-driven trading workflows.

Critical reading order:
1) This file (understand ground rules and current status)
2) docs/PROJECT_CONTEXT.md (project goals, architecture, repository layout)
3) docs/VERSIONING_RULES.md (version bump policy and release checklist)
4) docs/llm/HANDOFF.md (authoritative state and priorities)
5) docs/AGENT_REFERENCE.md (detailed analyst and system component roles)

## CRITICAL RULES (NON-NEGOTIABLE)

Language policy
- All code and documentation: English only
- Conversation with the user: Spanish only
- Comments in code: English only
- File names: English only

Documentation update rules
- Mandatory: every code or documentation change requires updating docs/llm/HANDOFF.md
- Mandatory: every session must append an entry to docs/llm/HISTORY.md
- HISTORY format: YYYY-MM-DD - [LLM_NAME] - [Brief summary] - Files: [list] - Version impact: [yes/no + which]

Commit message policy
- Mandatory: every LLM response with code changes must end with suggested commit information
- Format: "## Commit Info\n**Title:** [concise commit title]\n**Description:** [brief commit description explaining the change and its impact]"
- Keep commit titles under 72 characters, descriptions under 200 characters
- Both title and description must be in English
- Highlight user-facing impact rather than implementation trivia

Version management
- Always check the `version` field in `pyproject.toml` before modifying any release-sensitive files
- Never change versions without reviewing docs/VERSIONING_RULES.md
- Sync the version across all artifacts (code, packaging, Docker tags) when bumping

Environment files
- Never commit `.env`; it must stay local and untracked
- `.env.example` is the authoritative template; update it when new variables are required
- If a new secret is needed, document it in docs/llm/HANDOFF.md and coordinate with the user

## CURRENT FOCUS (synced from HANDOFF.md)

Source of truth: docs/llm/HANDOFF.md. Snapshot at last update:
- Last Updated: 2025-09-21 - ChatGPT
- Working on: Establishing a documentation baseline for the AI Hedge Fund repo
- Status: Documentation scaffold and README alignment completed; workflow-specific docs still pending

Top priorities (see HANDOFF for details):
1) Expand workflow docs covering CLI vs web application runtimes
2) Prepare testing guidance for risk and portfolio agents
3) Evaluate changelog strategy for future releases

Do not touch (without explicit request):
- Core trading logic under `src/agents/`
- Production Docker and deployment assets under `docker/`

## QUICK NAVIGATION

- Project Overview: docs/PROJECT_CONTEXT.md
- Version Rules: docs/VERSIONING_RULES.md
- Agent Reference: docs/AGENT_REFERENCE.md
- Current Work State: docs/llm/HANDOFF.md
- Change History: docs/llm/HISTORY.md

## LLM-TO-LLM COMMUNICATION

When handing off to another LLM:
1) Update docs/llm/HANDOFF.md with the current state
2) Append an entry to docs/llm/HISTORY.md summarizing your work
3) Ensure the snapshot above matches the latest HANDOFF state

## GETTING STARTED CHECKLIST

- [ ] Read this entire file
- [ ] Read PROJECT_CONTEXT.md
- [ ] Read VERSIONING_RULES.md
- [ ] Read current HANDOFF.md
- [ ] Confirm your task with the user
- [ ] Implement changes (code or docs)
- [ ] Update HANDOFF.md before finishing
- [ ] Append an entry to HISTORY.md

---

IMPORTANT: No change is complete until HANDOFF and HISTORY are updated.

