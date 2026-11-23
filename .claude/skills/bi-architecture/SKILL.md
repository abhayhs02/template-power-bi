---
name: bi-architecture
description: >
  Coordinates enterprise Power BI architecture by translating business
  requirements into an implementation-ready solution covering analytical
  processes, semantic-model boundaries, dimensional modeling, KPI semantics,
  source and refresh strategy, row-level security, performance architecture,
  and report information architecture. Use for new Power BI projects,
  substantial architecture changes, new analytical processes, new KPI
  families, security changes, source-strategy changes, or architecture reviews.
---
 
# Power BI Architecture
 
## Purpose
 
Use this skill to transform business requirements into an approved,
implementation-ready Power BI architecture.
 
This is the coordinating architecture skill for the BI Architect. It selects
and combines the relevant specialist skills, records architecture decisions,
and prepares bounded handoffs for implementation agents.
 
It does not implement:
 
- Power Query M
- TMDL tables or relationships
- production DAX
- calculation groups
- PBIR report definitions
- Power BI theme JSON
- deployment pipelines
 
## Specialist Skill Routing
 
Load only the skills materially relevant to the request.
 
- `dimensional-modeling`: grains, facts, dimensions, relationships, bridges,
  conformed dimensions, date architecture, and semantic-model boundaries.
- `kpi-semantic-design`: KPI meaning, populations, calculations, aggregation,
  time behavior, targets, thresholds, dependencies, and edge cases.
- `power-bi-source-strategy`: source authority, storage mode, refresh,
  incremental refresh, history, gateway, folding, and parameterization.
- `rls-security-design`: secured entities, security grain, identity mappings,
  static/dynamic RLS, hierarchy, access exceptions, and test personas.
- `power-bi-performance-architecture`: scale, cardinality, VertiPaq risks,
  partitions, aggregations, concurrency, DAX risks, and report query load.
 
Do not load every specialist skill for a trivial request.
 
## When to Use
 
Use for:
 
- new Power BI solutions
- new analytical business processes
- substantial semantic-model changes
- new fact or dimension tables
- new KPI families
- relationship-architecture changes
- source or refresh changes
- storage-mode decisions
- RLS changes
- architecture reviews
- conflicts discovered during implementation
 
Do not run the full workflow for isolated spelling, formatting, label,
documentation-only, or already-approved implementation corrections.
## Required Context
 
Before designing architecture:
 
1. Read the repository `CLAUDE.md`.
2. Read available business requirements and acceptance criteria.
3. Read current architecture and KPI documents.
4. Inspect relevant existing PBIP, TMDL, PBIR, M, and DAX source.
5. Review existing architecture decisions.
6. Separate confirmed facts, assumptions, and unresolved questions.
7. Load only the required specialist skills.
 
Do not redesign an existing solution before understanding it.
 
## Architecture Workflow
 
### 1. Business Outcome
 
Determine:
 
- business problem
- decisions supported
- intended users and personas
- analytical questions
- required KPIs and dimensions
- reporting frequency and freshness
- historical requirements
- security and performance expectations
- target handover environment
 
If the business outcome is materially unclear, return BLOCKED.
 
### 2. Analytical Processes
 
Identify each distinct analytical process. Do not merge processes with
different grains into one fact table merely for convenience.
 
### 3. Semantic Architecture
 
Use `dimensional-modeling` when required. Every fact must state:
 
> One row represents...
 
Define facts, dimensions, conformed dimensions, role-playing dimensions,
bridges, security tables, date architecture, model boundaries, and all
relationships with cardinality, direction, active status, and rationale.
 
Prefer star schemas, one-to-many relationships, single-direction filtering,
explicit Date dimensions, and business-readable names.
 
Document exceptions for many-to-many, bidirectional filtering, fact-to-fact
relationships, bridges, inactive relationships, and snowflakes.
 
### 4. KPI Architecture
 
Use `kpi-semantic-design` when required. Define each material KPI's business
question, meaning, logical formula, populations, aggregation, time behavior,
target, thresholds, dimensions, edge cases, authority, and dependencies.
 
Do not write production DAX or invent KPI semantics.
 
### 5. Source and Refresh Architecture
 
Use `power-bi-source-strategy` when required. Define source authority, volume,
growth, freshness, frequency, history, storage mode, incremental refresh,
late-arriving data, gateway dependency, folding expectations, parameters,
source load, and failure behavior.
 
Prefer Import when it satisfies the requirement. DirectQuery requires explicit
justification.
 
### 6. Security Architecture
 
Use `rls-security-design` when required. Define protected data, secured entity,
security grain, identity, authorization source, RLS approach, multi-entity and
hierarchical access, privileged roles, filter path, default behavior, and test
personas.
Do not assume workspace access replaces RLS.
 
### 7. Performance Architecture
 
Use `power-bi-performance-architecture` when required. Evaluate volume, growth,
history, grain, unnecessary and high-cardinality columns, data types,
relationships, storage mode, partitions, aggregations, DAX risk, report query
load, concurrency, refresh window, and measurable acceptance targets.
 
### 8. Report Information Architecture
 
Define audience, purpose, executive versus operational use, page hierarchy,
analytical journey, KPI priority, navigation, drill-through, tooltip, detail,
mobile, accessibility, and exception-analysis requirements.
 
Do not implement PBIR.
 
### 9. Architecture Decisions
 
Use ADRs for decisions that affect multiple agents, change model or security
architecture, introduce exceptions, change KPI meaning, introduce DirectQuery,
or materially affect performance and maintainability.
 
ADR structure:
 
- Context
- Decision
- Alternatives
- Rationale
- Consequences
- Status: Proposed, Accepted, or Superseded
 
### 10. Implementation Handoffs
 
Provide bounded handoffs:
 
- Data Modeler: grains, facts, dimensions, keys, relationships, sources, data
  types, refresh, folding, security tables, and data-quality risks.
- DAX Engineer: KPI contracts, populations, aggregation, time behavior,
  targets, thresholds, edge cases, dependencies, and test scenarios.
- Visual Designer: audience, questions, page hierarchy, KPI priority,
  navigation, drill-through, tooltips, accessibility, and performance limits.
- BI Auditor: decisions, exceptions, security, refresh, risks, validation rules,
  and expected semantic behavior.
 
## Mandatory Principles
 
Always:
 
- start with business outcome
- define grain before facts
- prefer star schemas and conformed dimensions
- prefer one-to-many and single-direction relationships
- define KPI semantics before DAX
- define security before RLS implementation
- identify source authority
- separate assumptions from facts
- document material exceptions
- preserve approved architecture unless changing it explicitly
 
Never:
 
- design from visuals backward
- copy a transactional schema without analytical redesign
- approve ambiguous fact grain or filter paths
- invent KPI semantics, targets, thresholds, owners, or security rules
- choose DirectQuery only because data is large
- hide blockers inside implementation instructions
- implement M, TMDL, DAX, PBIR, or theme JSON from this skill
 
## Architecture Artifacts
 
Create or update only required artifacts:
 
- `docs/architecture/solution-architecture.md`
- `docs/architecture/semantic-model.md`
- `docs/architecture/relationship-design.md`
- `docs/architecture/security-design.md`
- `docs/architecture/refresh-architecture.md`
- `docs/architecture/performance-architecture.md`
- `docs/architecture/report-information-architecture.md`
- `docs/architecture/architecture-decisions.md`
- `docs/requirements/kpi-catalogue.md`
 
Do not create empty or duplicate documents.
 
## Status Rules
 
Return `ARCHITECTURE STATUS: READY` only when implementation agents can
proceed without inventing material business rules.
 
Return `ARCHITECTURE STATUS: BLOCKED` when unresolved decisions affect the
business objective, process, grain, KPI meaning, source authority,
relationships, security, storage, refresh, result accuracy, or feasibility.
 
## Required Final Response
 
Return:
 
- Architecture Status: READY or BLOCKED
- Architecture Summary
- Confirmed Requirements
- Skills Used
- Files Created or Changed
- Key Decisions
- Architecture Exceptions
- Assumptions
- Risks
- Open Questions
- Handoff Readiness
- Recommended Next Step
