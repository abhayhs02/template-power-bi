---
name: tmdl-semantic-modeling
description: Implements and reviews approved Power BI semantic-model structures in TMDL, including tables, columns, hierarchies, relationships, partitions, expressions, roles, descriptions, formatting, hidden states, sort-by columns, data categories, storage metadata, and source-control-safe organization. Does not invent architecture or KPI semantics.
---
 
# TMDL Semantic Modeling
 
## Purpose
 
Translate approved semantic-model architecture and Power Query outputs into clean, stable, reviewable TMDL source.
 
## Primary consumers
 
- `data-modeler`: implement tables, columns, relationships, partitions, roles, metadata.
- `dax-engineer`: implement measures and calculation groups within owned scope.
 
## Supporting consumers
 
- `bi-auditor`: inspect quality and compliance.
- `pr-reviewer`: inspect diffs.
 
## Ownership rule
 
This skill defines a technical method. Agent role ownership determines which TMDL objects may be changed.
 
## Required inputs
 
- approved semantic-model architecture
- table/column/source mapping
- relationship design
- data types/formats
- hierarchy/sort-by/data-category requirements
- partition/refresh strategy
- RLS/security design when applicable
- current TMDL organization and conventions
 
## Workflow
 
### 1. Discover TMDL structure
 
Use actual repository files to identify model definition, tables, measures, expressions, relationships, roles, partitions, cultures/translations when present, and organization conventions.
 
### 2. Establish object scope
 
List objects to add/update/remove, owning agent, approved design source, and protected objects.
 
### 3. Implement tables and columns
 
Define approved names, source/expression bindings, data types, formats, descriptions, hidden states, sort-by, data categories, summarize behavior where applicable, and key-related metadata.
 
Avoid importing undocumented/unrequired columns.
 
### 4. Implement hierarchies
 
Use business meaningful levels and approved order. Avoid artificial hierarchies with no user value.
 
### 5. Implement relationships
 
Match approved from/to column, cardinality, filter direction, active status, and rationale. Do not add bidirectional/many-to-many/fact-to-fact behavior without explicit approval.
 
### 6. Implement partitions and expressions
 
Match approved Power Query and refresh/storage strategy. Preserve environment neutrality and existing organization.
 
### 7. Implement roles/security structures
 
Only when explicitly included in the task and approved security architecture. Do not embed real user mappings or invent filters.
 
### 8. Preserve source stability
 
Follow repository TMDL organization. Avoid mass rewrites, arbitrary object reordering, unrelated formatting churn, and regenerated metadata unless required.
 
### 9. Validate
 
Use available TMDL parsing, Tabular Editor/Power BI Desktop validation, repository scripts, relationship checks, object-reference checks, RLS checks, and Git diff review.
 
## Rules
 
- Architecture determines structure.
- KPI contracts determine meaning.
- Data Modeler owns structural TMDL; DAX Engineer owns measure/calculation TMDL.
- Do not move ownership silently.
- Do not put secrets or environment credentials in TMDL.
- Do not manually invent unknown TMDL syntax.
 
## Stop and escalate when
 
- approved architecture/source mapping is incomplete
- required types/keys/relationships conflict
- source constraints invalidate approved grain
- requested syntax/object is unsupported or unknown
- implementation requires unapproved relationship/security/storage changes
- mandatory validation is unavailable
 
## Required output
 
### Status
 
Completed | Blocked | Needs decision
 
### TMDL objects in scope
 
List objects, owner, action, and approved source.
 
### Implementation summary
 
List tables, columns, hierarchies, relationships, partitions, expressions, roles, and metadata changed.
 
### Files changed
 
List exact paths and purpose.
 
### Validation
 
List parser/tool/script/Desktop checks, result, and evidence.
 
### Diff stability
 
Confirm unrelated source and identifiers were preserved.
 
### Dependencies and handoff
 
List DAX/report/audit/review dependencies and next owner.
