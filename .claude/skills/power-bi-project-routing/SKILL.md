---
name: power-bi-project-routing
description: Classifies incoming Power BI requests into architecture, semantic-model, DAX, visual-design, audit, review, documentation, or cross-repository work. Returns accountable specialists, prerequisites, owned paths, ordering, safe parallelism, evidence, and approval gates. Use for every request handled by bi-orchestrator. This skill routes work and never performs specialist work.
---

# Power BI Project Routing

## Purpose
Turn a user request into a bounded, evidence-driven Power BI delivery plan without solving the specialist work inside the routing step.

## Primary consumer
- `bi-orchestrator`

## Authority boundary
This skill may:
- classify work
- identify owners
- identify dependencies
- recommend sequence and parallelism
- identify required evidence and gates
- detect cross-repository scope

This skill must not:
- define business rules
- design the model
- define KPI semantics
- write M, TMDL, DAX, PBIR, theme, audit findings, review findings, or documentation
- expand the orchestrator's authority

## Inputs
- user request
- `CLAUDE.md`
- current repository structure
- existing approved requirements, architecture, KPI, RLS, and design artifacts
- current branch/status when implementation planning is requested
- relevant prior specialist outputs

## Work classifications
Classify each requested outcome into one or more areas:

### Architecture
Use when the request introduces or changes:
- business questions or acceptance criteria
- analytical grain
- fact/dimension boundaries
- source/storage mode or refresh approach
- KPI definition, target, threshold, exclusion, or directionality
- RLS/security architecture
- cross-report/model architecture
- material performance architecture

Owner: `bi-architect`

### Semantic model and Power Query
Use when the request changes:
- data ingestion or M transformations
- tables, columns, data types, metadata, hierarchies
- relationships or cardinality
- partitions, incremental refresh implementation, storage settings
- approved RLS structures

Owner: `data-modeler`

### DAX
Use when the request changes:
- measures
- calculation groups/items
- time intelligence
- format strings or dynamic formatting
- DAX performance
- measure organization or metadata

Owner: `dax-engineer`

### Visual design and PBIR
Use when the request changes:
- report-page composition
- visual types or formatting
- layout, hierarchy, typography, spacing, or color
- slicers, navigation, bookmarks, tooltips, drill-through
- accessibility
- PBIR or theme JSON

Owner: `visual-designer`

### Audit and deterministic quality checks
Use when the request requires:
- BPA-style checks
- relationship/model quality checks
- DAX formatting/performance rule checks
- report-source or theme checks
- release validation evidence

Owner: `bi-auditor`

### Independent review
Use when a complete implementation package requires adversarial review.

Owner: `pr-reviewer`

### Documentation
Use when accepted changes need:
- README/setup
- architecture summary
- KPI catalog
- data dictionary
- report/user/admin guide
- release or handover documentation

Owner: `doc-writer`

### Cross-repository dependency
Use when Power BI requires:
- an external API or data pipeline implementation
- Power Apps/Power Automate work
- upstream source-system changes
- infrastructure or capability owned elsewhere

Action: report the dependency and require user authorization before contacting the owning repository orchestrator.

## Routing procedure

### 1. Parse the outcome
Extract:
- desired business outcome
- requested deliverable
- explicit constraints
- priority
- acceptance criteria supplied by the user
- requested deadline only as context; do not invent scheduling commitments

### 2. Inspect existing artifacts
Determine whether approved requirements and architecture already cover the change.

Do not route directly to implementation when a required governing decision is missing.

### 3. Decompose by ownership
Create the smallest bounded tasks that preserve one accountable owner per artifact.

Avoid tasks such as "build the dashboard" when they combine architecture, DAX, PBIR, validation, and documentation.

### 4. Determine prerequisites
Examples:
- KPI definition before DAX
- grain/relationship design before model implementation
- model fields and measures before PBIR implementation
- design-material governance before visual design
- implementation and audit evidence before final PR review
- accepted source artifacts before final documentation

### 5. Determine sequence and parallelism
Parallelize only when tasks:
- have approved shared inputs
- own separate artifacts
- do not depend on unfinished outputs
- have a defined integration point

### 6. Map gates and evidence
For every task identify:
- gate served
- expected files/artifacts
- deterministic or review evidence
- user approval requirement
- rework owner

### 7. Detect missing routing information
Ask only routing-level questions.

Route domain questions to the owning specialist rather than answering them inside routing.

## Risk classification
Use:

### Low
- documentation typo
- non-functional metadata correction
- small formatting change covered by existing design rules

Expected path: owner → applicable validation → review according to repository policy.

### Medium
- new measure under an approved KPI definition
- page redesign using existing model and design standards
- source transformation or relationship change with bounded impact

Expected path: owner → audit/validation → PR review → user acceptance as applicable.

### High
- new or changed KPI meaning
- grain or relationship architecture change
- RLS change
- storage mode/source strategy change
- major performance change
- broad report redesign without complete design direction
- production-sensitive or cross-repository dependency

Expected path: architect/user approval → implementation → full validation/audit → independent review → explicit user approval.

## Output format

### Classification
For each work area:
- area
- reason
- accountable agent
- risk

### Prerequisites
- approved artifact or decision
- current availability
- owner if missing

### Execution plan
For each task:
- task ID
- goal
- agent
- inputs
- owned paths
- in scope
- out of scope
- gate served
- expected evidence
- dependencies

### Parallelism
- tasks safe to run in parallel
- tasks that must remain sequential
- reason

### User decisions
- routing-level approvals only

### Cross-repository dependencies
- capability needed
- authorization status
- owning orchestrator when known

### Next delegation
- first agent
- concise delegation brief

## Completion criteria
- every outcome classified
- every artifact has one accountable owner
- prerequisites and sequence are explicit
- evidence and gates are mapped
- cross-repository scope is identified
- no specialist solution was created during routing
