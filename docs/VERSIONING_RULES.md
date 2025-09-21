# Versioning Rules

This project follows Semantic Versioning (SemVer) for all published artifacts. The canonical version lives in `pyproject.toml` under the `version` field.

## Version Number Format

```
MAJOR.MINOR.PATCH
```

- **MAJOR** – Increment when making incompatible API changes, removing functionality, or altering the workflow contract in a breaking way (e.g., state schema changes, CLI flag removals).
- **MINOR** – Increment when adding functionality in a backward compatible manner, such as new agents, additional CLI flags, or new web routes.
- **PATCH** – Increment for backward compatible bug fixes, UI polish, or documentation-only releases that require publishing a new package/image.

## When to Bump the Version

1. Changes that require publishing a new Python package build or Docker image.
2. Modifications to agent workflows that impact serialized state or model expectations.
3. CLI or web API changes that affect user interactions.
4. Any release communicated to downstream users or stakeholders.

Pure documentation updates that do not trigger a release do **not** require a version bump.

## Bump Checklist

Before updating the version:

- [ ] Review recent commits and confirm the correct (MAJOR/MINOR/PATCH) increment.
- [ ] Update `pyproject.toml` with the new version.
- [ ] Search for other hard-coded version references (Docker tags, docs, badges) and update them.
- [ ] Run the full automated test suite (`poetry run pytest`).
- [ ] Update docs/llm/HISTORY.md to mention the release and its scope.
- [ ] Communicate changes in the project changelog (if applicable).

## Release Notes

- Capture release highlights in the repository Changelog or Release notes on GitHub.
- Focus on user-visible behavior: new features, fixes, and compatibility notes.
- Link to relevant documentation updates when possible.

## Tagging Guidance

- Create a Git tag matching the new version (`vMAJOR.MINOR.PATCH`) after tests pass.
- Ensure CI/CD workflows that rely on tags are triggered and succeed before announcing the release.

Adhering to this policy keeps downstream consumers aligned and reduces integration surprises.

