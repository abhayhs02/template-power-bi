# template-power-bi

## Repository Purpose

This repository is the reusable agentic development template for
enterprise Power BI projects.

Power BI development should use Power BI Project (PBIP) source format
where supported so semantic-model and report definitions remain
readable, reviewable, testable, and version-controlled.

Primary source artifacts include:

- `.pbip` project definitions
- TMDL semantic-model definitions
- PBIR report definitions
- Power Query M
- DAX measures
- Theme JSON
- architecture documentation
- validation assets
- release packaging scripts

A `.pbix` file is not the primary Git source artifact.

---

# Operating Model

The repo-level `bi-orchestrator` is the single user entry point.

The user should not normally need to select specialist agents manually.

The orchestrator:

1. understands the request;
2. reads repository context;
3. determines which specialists are required;
4. delegates work;
5. coordinates dependent tasks;
6. invokes validation;
7. requests independent review;
8. prepares the final result for user approval.

Specialist agents operate only within their assigned responsibilities.

---

# Agent Workforce

The Power BI workforce consists of:

1. `bi-orchestrator`
2. `bi-architect`
3. `data-modeler`
4. `dax-engineer`
5. `visual-designer`
6. `bi-auditor`
7. `pr-reviewer`
8. `doc-writer`

Only agents defined under `.claude/agents/` may act as repository
specialists.

---

# Responsibility Boundaries

## bi-orchestrator

Owns:

- task intake
- planning
- agent routing
- dependency coordination
- Git worktree coordination
- quality-gate sequencing
- cross-repository requests
- release coordination

Does not replace specialist judgment.

## bi-architect

Owns:

- requirements interpretation
- analytical business processes
- fact grain
- dimensional architecture
- fact and dimension design
- KPI contracts
- relationship architecture
- semantic-model boundaries
- RLS architecture
- refresh architecture
- report information architecture
- architecture decisions

Does not normally implement TMDL, M, DAX or PBIR.

## data-modeler

Owns:

- Power Query M
- TMDL tables
- columns
- data types
- hierarchies
- relationships
- model metadata
- source ingestion design

## dax-engineer

Owns:

- measures
- calculation groups
- time intelligence
- dynamic formatting
- advanced DAX
- measure optimization

## visual-designer

Owns:

- PBIR report definitions
- report-page implementation
- navigation
- bookmarks
- drill-through
- tooltip experiences
- theme application
- accessibility implementation

## bi-auditor

Owns:

- semantic-model quality checks
- relationship checks
- cardinality risks
- performance risks
- RLS checks
- DAX quality checks
- report metadata checks

## pr-reviewer

Owns independent review.

The reviewer must not implement the work being reviewed.

## doc-writer

Owns milestone documentation including:

- data dictionaries
- KPI catalogues
- architecture documentation
- release notes
- user documentation
- handover documentation

---

# Architecture-First Rule

For material Power BI development, use:

Business Requirement

→ BI Architecture

→ Semantic Model

→ DAX

→ Report Design

→ Audit

→ PR Review

→ Release

Implementation must not proceed while unresolved architectural
decisions materially affect downstream work.

Minor isolated corrections do not require unnecessary architecture
ceremony.

---

# Architecture Authority

The `bi-architect` defines business meaning.

Implementation agents must not silently redefine:

- KPI semantics
- fact grain
- relationship architecture
- security requirements
- business dimensions
- source-of-truth rules

If implementation exposes a flaw in the architecture, return the issue
to the architect through the orchestrator.

---

# Repository Boundaries

This folder is an independent Git repository.

Its parent project workspace is not assumed to be a Git repository.

Sibling repositories may belong to the same logical project.

Examples:

inventory-management-power-bi

inventory-management-power-apps

inventory-management-power-automate

inventory-management-web

Cross-repository collaboration occurs orchestrator-to-orchestrator.

Specialist agents must not directly command agents in another
repository.

---

# Cross-Repository Access

Cross-repository work requires user authorization.

When another project type is required:

1. Detect the dependency.
2. Inform the user.
3. Recommend the appropriate template.
4. Propose a repository name.
5. Wait for the user to create or attach the repository.
6. Record the dependency in `project.yaml`.
7. Communicate with the sibling repository's orchestrator.

Cross-repository access is read-only by default.

Write access requires explicit authorization.

---

# Source-Control Rules

Prefer text-based, diffable Power BI artifacts.

Expected structure:

powerbi/
├── ProjectName.pbip
├── ProjectName.Report/
└── ProjectName.SemanticModel/

Do not unnecessarily modify unrelated files.

Do not commit generated temporary files.

Do not rewrite unrelated architecture during isolated changes.

---

# Security Rules

Never commit:

- passwords
- API keys
- access tokens
- private keys
- production credentials
- tenant secrets
- gateway credentials
- authentication artifacts
- personal information
- confidential enterprise datasets
- production dataset exports

Personal-development environments must use:

- generic schemas
- metadata
- synthetic data
- anonymized test data

Company-specific connections are configured during enterprise
handover.

---

# Agent Quality Rules

Every agent must:

1. Read `CLAUDE.md`.
2. Read relevant project documentation.
3. Read applicable skills.
4. Understand existing implementation before modifying it.
5. Stay inside role boundaries.
6. State material assumptions.
7. Preserve approved architecture.
8. Validate its work.
9. Record unresolved issues.
10. provide downstream agents with usable evidence.

Agents must not invent missing business semantics.

---

# Skills

Reusable specialist knowledge belongs under:

`.claude/skills/`

Skills should contain reusable workflows and domain standards.

Agent files should define:

- identity
- responsibility
- authority
- workflow
- skill usage
- handoff requirements

Avoid copying large bodies of specialist knowledge directly into
multiple agent definitions.

---

# Validation

Prefer deterministic validation over model judgment whenever possible.

Examples include:

- JSON schema validation
- TMDL parsing
- PBIR validation
- formatting checks
- best-practice rules
- secret scanning
- Git diff inspection
- release-package verification

Agents interpret validation output but do not replace deterministic
checks when reliable tooling exists.

---

# Review Separation

A builder must not approve its own implementation.

Material implementations should pass:

Implementation

→ Validation

→ BI Audit when applicable

→ PR Review

→ Human approval where required

---

# Human Authority

The user remains the final authority for:

- architecture approval
- significant scope changes
- creation of sibling repositories
- cross-repository write access
- security-sensitive decisions
- enterprise migration
- production publishing
- release approval

Agents may recommend these actions.

They must not silently perform them.

---

# Documentation Locations

Architecture:

`docs/architecture/`

Requirements:

`docs/requirements/`

Reusable project standards:

`standards/`

Agent definitions:

`.claude/agents/`

Agent skills:

`.claude/skills/`

Validation scripts:

`scripts/`

Tests:

`tests/`

Release artifacts:

`release/`

---

# Current Template Status

This repository is a reusable Power BI agentic-development template.

Technology-specific Power BI source should be initialized only after
actual project requirements are known.