---
name: power-bi-quality-audit
description: Runs and structures independent Power BI quality audits across PBIP, TMDL, Power Query, DAX, PBIR, themes, RLS, performance metadata, repository hygiene, and validation evidence. Use after material implementation and before PR review. Produces evidence-backed findings and an audit-gate recommendation; never implements fixes.
---
 
# Power BI Quality Audit
 
## Purpose
 
Provide a repeatable audit method that combines deterministic checks with bounded expert inspection.
 
## Primary consumer
 
- `bi-auditor`
 
## Inputs
 
- audit scope and changed files
- approved architecture, KPI, source, security, and performance artifacts
- approved exceptions
- actual PBIP artifact map
- available validation scripts/tools
- implementation evidence
 
## Procedure
 
### 1. Map audit requirements
 
For the changed areas, identify applicable checks for:
 
- semantic-model structure
- Power Query/source strategy
- DAX quality/performance
- RLS/security
- PBIR/theme/report source
- design compliance
- repository security/hygiene
- documentation/evidence completeness
 
### 2. Discover actual source
 
Use `pbip-project-navigation` and do not assume fixed paths.
 
### 3. Run deterministic checks
 
Run available approved checks. Candidate evidence may include:
 
- JSON parse and schema checks
- repository scripts
- Tabular Editor 2 BPA, when installed and compatible
- DAX Studio/VertiPaq Analyzer reports supplied for performance scope
- Power BI Desktop open/refresh evidence
- secret scans
- Git diff/status
 
Record unavailable checks. Do not treat them as passed.
 
### 4. Audit semantic model
 
Evaluate grain alignment, model boundaries, relationships, cardinality, filter direction, Date design, bridges, hidden fields, types, formats, descriptions, sort-by, hierarchies, partitions, storage mode, and approved exceptions.
 
### 5. Audit performance metadata
 
Evaluate unnecessary/high-cardinality columns, excessive precision, calculated artifacts, relationship keys, aggregation/partition strategy, source folding evidence, and model-size indicators where evidence exists.
 
### 6. Audit DAX metadata and patterns
 
Evaluate KPI-contract traceability, measure organization, descriptions, format strings, duplicate logic, blank/division behavior, expensive patterns, and calculation-group implications.
 
### 7. Audit RLS
 
Evaluate role definitions, secured entity, propagation, default behavior, mapping-data safety, approved exceptions, and test-persona evidence.
 
### 8. Audit PBIR/theme/report source
 
Evaluate JSON validity, source churn, IDs/references, page/bookmark/tooltip/drill-through/theme integrity, design-material evidence, and accessible/performance concerns relevant to the scope.
 
### 9. Audit repository hygiene
 
Evaluate secrets/sensitive values, personal paths, generated artifacts, inappropriate binaries, unrelated files, and missing evidence/doc updates.
 
### 10. Classify and route findings
 
Use BLOCKER, HIGH, MEDIUM, LOW, INFO. Assign the owning agent and objective acceptance condition.
 
## Audit rules
 
- Evidence must be identified.
- Style preference alone is not a finding unless an approved standard exists.
- Approved exceptions must be honored within their exact scope.
- A finding must identify the user, business, performance, security, maintenance, or release impact.
- Findings must be reproducible where possible.
- Do not fix the issue while auditing.
 
## Audit-gate rules
 
- BLOCKER/HIGH or failed mandatory check → failed gate.
- Required unavailable evidence → blocked gate when policy makes it mandatory.
- MEDIUM/LOW may pass only when repository policy permits and the follow-up is visible.
- INFO never blocks.
 
## Required output
 
### Audit status
 
PASS | PASS WITH FINDINGS | FAIL | BLOCKED
 
### Scope and standards
 
List changed areas, approved standards, exceptions, and required checks.
 
### Executed evidence
 
List tool/check, result, and evidence.
 
### Findings
 
For each: ID, severity, category, path/object, standard, evidence, impact, owner, acceptance condition.
 
### Coverage and limitations
 
List audited areas, excluded areas, unavailable checks, manual checks, and evidence gaps.
 
### Audit-gate recommendation
 
PASSED | PASSED WITH NON-BLOCKING FINDINGS | FAILED | BLOCKED
 
### Re-audit plan
 
List exact checks/evidence required after remediation.
