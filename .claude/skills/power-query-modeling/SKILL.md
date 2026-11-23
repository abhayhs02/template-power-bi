---
name: power-query-modeling
description: Implements approved Power BI source ingestion and transformation logic in Power Query M, including parameterization, explicit typing, folding-aware transformations, joins, deduplication and error handling according to approved business rules, incremental-refresh filters, source privacy boundaries, and source-to-target traceability. Does not choose source authority, grain, KPI semantics, or storage strategy.
---
 
# Power Query Modeling
 
## Purpose
 
Implement reliable, portable, refreshable Power Query transformations from approved source strategy and semantic-model requirements.
 
## Primary consumer
 
- `data-modeler`
 
## Required inputs
 
- approved source inventory and authority
- source schema and keys
- target table/column design
- approved grain and data-quality rules
- storage/refresh strategy
- required freshness/history
- incremental-refresh requirements
- environment parameter requirements
- security/privacy constraints
 
## Workflow
 
### 1. Inspect current queries
 
Locate queries, shared expressions, parameters, source steps, dependencies, and existing conventions. Do not duplicate an existing governed query without reason.
 
### 2. Parameterize environment values
 
Use parameters for approved environment-dependent endpoints such as server, database, site root, file root, or API base URL.
 
Never store credentials, tokens, passwords, gateway secrets, or private keys.
 
### 3. Minimize extraction
 
Select only required tables, rows, and columns. Push filtering/projection to the source when approved and folding-capable.
 
### 4. Apply explicit types
 
Set intentional data types after source discovery and transformations. Avoid locale-dependent ambiguous conversions. Explain precision/timezone decisions when material.
 
### 5. Implement transformations
 
Use readable named steps. Handle joins, expansion, grouping, pivot/unpivot, parsing, normalization, and calculations according to approved logic.
 
Do not hide business rules inside unexplained technical transformations.
 
### 6. Handle data quality
 
Implement approved behavior for:
 
- nulls
- errors
- duplicates
- malformed rows
- missing keys
- late-arriving records
- schema drift
- invalid dates/numbers
 
If behavior is not approved and affects results, stop rather than guessing.
 
### 7. Preserve folding
 
Where required:
 
- keep foldable filters/types/column selection early
- identify the step where folding stops
- avoid row-by-row custom logic over large sources without approved reason
- provide source-query or folding evidence when available
 
Folding is a means, not a blanket requirement. Document justified non-folding logic.
 
### 8. Implement incremental-refresh range logic
 
When approved, implement compatible RangeStart/RangeEnd filtering and ensure the intended source/date column and folding behavior support the architecture.
 
### 9. Protect privacy and portability
 
Avoid combining sources in ways that violate privacy/security boundaries. Keep development data synthetic or approved. Keep paths portable.
 
### 10. Validate
 
Run available syntax/parse, repository, refresh, row-count, duplicate/key, type, and folding checks. Compare source/target expectations where possible.
 
## Quality rules
 
- readable named steps
- no unnecessary query duplication
- no embedded credentials/private paths
- explicit types
- controlled error handling
- approved transformation semantics
- folding awareness
- narrow source-control diff
 
## Stop and escalate when
 
- authoritative source or key is unclear
- source schema contradicts approved target/grain
- a deduplication or exclusion rule is missing
- required folding cannot be achieved within approved architecture
- credentials/private data would be required in Git
- source access/validation is unavailable and mandatory
 
## Required output
 
### Status
 
Completed | Blocked | Needs decision
 
### Queries and sources
 
List query, source, purpose, dependencies, and parameters.
 
### Transformations
 
List major steps and approved rule/source.
 
### Data-quality handling
 
List null/error/duplicate/invalid-record behavior.
 
### Folding and refresh evidence
 
List folded/non-folded boundary, incremental-refresh logic, and available evidence.
 
### Files changed
 
List exact repository-relative paths.
 
### Validation
 
List check, result, evidence, and unavailable checks.
 
### Handoff
 
Provide target tables/columns, constraints, risks, and next owner.
