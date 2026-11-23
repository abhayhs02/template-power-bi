---
name: power-bi-pr-review
description: Performs independent, evidence-based review of Power BI pull-request or branch changes across requirements, architecture, Power Query, TMDL, DAX, PBIR, themes, design-material compliance, RLS, performance, repository security, documentation, audit evidence, and release impact. Use after implementation and validation are complete. Produces actionable findings and an approval recommendation; never implements fixes.
---
 
# Power BI Pull Request Review
 
## Purpose
 
Determine whether a Power BI change meets approved requirements and quality gates without violating separation of duties.
 
## Primary consumer
 
- `pr-reviewer`
 
## Required inputs
 
- approved task/scope and acceptance criteria
- base and head revisions/branches
- complete diff and changed-file list
- applicable architecture/KPI/source/RLS/design artifacts
- validation and BI audit evidence
- documentation and release-impact assessment
 
Missing scope or mandatory evidence is not a pass.
 
## Review workflow
 
### 1. Establish traceability
 
Map requirement → architecture/KPI/design rule → implementation file → validation evidence.
 
Identify unrelated/unexplained files.
 
### 2. Review architecture compliance
 
Check grain, facts/dimensions, relationship/cardinality/filter direction, source/storage, KPI semantics, RLS, performance, and approved exceptions.
 
Unapproved material architecture changes are blocking.
 
### 3. Review Power Query/model
 
Check source assumptions, parameters, folding risk, types, null/error handling, naming, duplication, relationships, cardinality, high-cardinality/model-size risk, hidden objects, RLS propagation, and incremental refresh.
 
### 4. Review DAX
 
Check KPI compliance, filter/context behavior, blank/zero/not-applicable handling, division/error safety, base-measure reuse, time-intelligence assumptions, format strings, expensive patterns, and calculation-group side effects.
 
### 5. Review PBIR/theme/design
 
Check:
 
- design-taste.md adherence
- proof of inspected references
- visual hierarchy/layout/spacing/color consistency
- analytical visual choice
- interaction and analytical states
- accessibility
- narrow PBIR/theme diff
- absence of unsupported schema/mass churn
 
### 6. Review security/hygiene
 
Check secrets, tokens, connection strings, credentials, private paths, sensitive data, tenant/workspace identifiers, RLS weakening, and unauthorized production actions.
 
Any committed secret or material security weakening is BLOCKER.
 
### 7. Review validation evidence
 
Record exact status of applicable:
 
- JSON/schema parsing
- repository scripts
- Power Query/TMDL/DAX checks
- BI quality audit/BPA
- reconciliation tests
- RLS tests
- Desktop open/refresh validation
- design/accessibility checks
- clean Git diff/status
 
Use Performed-Passed, Performed-Failed, Not performed, or Unavailable. Unavailable is not Passed.
 
### 8. Review documentation/release impact
 
Check updated README/setup, architecture, KPI catalogue, data dictionary, RLS/refresh guide, user guide, release notes, and handover where applicable.
 
### 9. Classify findings
 
Use exactly:
 
- `BLOCKER`: secret/security exposure, corrupt/unusable project, unapproved architecture/KPI/RLS change, incorrect business result, or required gate failure.
- `HIGH`: likely incorrect result, serious performance/design/security issue, missing mandatory validation, or major maintainability risk.
- `MEDIUM`: material maintainability, consistency, accessibility, operational, or documentation issue.
- `LOW`: non-blocking improvement.
- `QUESTION`: clarification; state whether blocking.
 
Every finding must be specific and actionable.
 
### 10. Make recommendation
 
- `APPROVE`: no blocking findings and required evidence present.
- `APPROVE WITH NON-BLOCKING FOLLOW-UPS`: only explicitly acceptable Medium/Low follow-ups.
- `CHANGES REQUIRED`: BLOCKER/HIGH, failed gates, or missing mandatory evidence.
- `BLOCKED`: review cannot be completed.
 
## Separation-of-duties rules
 
- Do not edit files.
- Do not suggest a review fix by secretly implementing it.
- Route findings to the owning agent.
- Require new evidence after remediation.
- Re-review only affected scope plus regression impact.
 
## Required output
 
### Review status
 
Completed | Blocked
 
### Scope and traceability
 
List task, acceptance criteria, base/head, changed files, and requirement-to-evidence mapping.
 
### Evidence evaluated
 
List evidence, result, limitation, and gate.
 
### Findings
 
For every finding include ID, severity, path/location, evidence, impact, owner, correction, and acceptance condition.
 
### Gate assessment
 
Assess architecture, implementation, validation/audit, design, security, and documentation/release gates.
 
### Recommendation
 
APPROVE | APPROVE WITH NON-BLOCKING FOLLOW-UPS | CHANGES REQUIRED | BLOCKED
 
### Re-review plan
 
List remediation owners, required evidence, and scope.
