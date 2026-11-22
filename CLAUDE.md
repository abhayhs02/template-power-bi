# template-power-bi

## Repository purpose
Power BI PBIP-oriented template for semantic models, TMDL, PBIR, themes, validation, and documentation.

## Operating rules
1. The repo-level orchestrator is the single user entry point.
2. The architect defines or updates architecture before material implementation.
3. Specialist agents may change only files within this repository unless the user explicitly authorizes cross-repository work.
4. Cross-repository work must be requested from the sibling repository's orchestrator.
5. The PR reviewer must not implement the change being reviewed.
6. The doc writer runs at meaningful milestones or when explicitly requested.
7. Never commit secrets, personal access tokens, connection references, or production credentials.
8. Prefer deterministic validation through scripts and CI workflows.

## Repository boundaries
- This folder is an independent Git repository.
- Its parent project workspace is not assumed to be a Git repository.
- Sibling repositories may be discovered through a future project manifest.

## Current status
Template scaffold only. Technology-specific source projects should be initialized only when the project requirements are known.
