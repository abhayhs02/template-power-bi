---
name: pbir-report-editing
description: Implements approved Power BI visual designs as narrow, source-control-friendly changes in existing PBIR report definitions and supported theme JSON. Use only after design-material governance and an approved visual-design specification are complete. Preserve identifiers and unrelated files, validate what can be validated, and never invent unknown PBIR schema or alter DAX/model semantics.
---
 
# PBIR Report Editing
 
## Purpose
 
Translate an approved design specification into controlled PBIR and theme changes.
 
## Primary consumer
 
- `visual-designer`
 
## Supporting consumers
 
- `pr-reviewer`: inspect PBIR/theme diffs without editing.
- `bi-auditor`: run applicable structural checks.
 
## Required inputs
 
- approved visual-design specification
- governed design-material summary
- current PBIP/PBIR source
- approved theme
- approved field/measure bindings
- protected files/areas
 
## Safety rules
 
- Inspect existing PBIR structure before editing.
- Preserve identifiers/references unless deliberate creation/removal requires change.
- Prefer narrow edits over complete rewrites.
- Avoid mass JSON reformatting or key reordering.
- Do not handcraft unknown schema from memory.
- Use existing repository patterns and installed-version-supported behavior.
- Do not edit DAX, M, TMDL architecture, RLS, or KPI definitions.
- Do not introduce secrets, local paths, tenant IDs, or workspace IDs.
 
## Workflow
 
### 1. Locate project artifacts
 
Use `pbip-project-navigation` to identify the PBIP entry point, report project, PBIR definitions, pages, visuals, theme, bookmarks/navigation, tooltip/drill-through artifacts, and mobile layout when present.
 
### 2. Establish baseline
 
Record branch/status, exact files in scope, existing structure, and clean diff baseline.
 
### 3. Map design to source
 
For every design requirement record page, object, property/theme token, expected behavior, and source design rule.
 
### 4. Implement narrowly
 
Change only approved:
 
- page and visual layout
- supported visual formatting
- titles, labels, surfaces, borders, spacing
- slicer/filter placement
- navigation/bookmark artifacts when understood
- tooltip/drill-through artifacts when understood
- theme JSON tokens
 
Do not change field bindings or interactions unless explicitly included in the approved specification and supported by existing artifacts.
 
### 5. Validate
 
Run available:
 
- JSON parse checks
- repository scripts
- schema-aware tooling
- Power BI Desktop open/save validation
- navigation/bookmark/tooltips/drill-through checks
- Git diff inspection
 
JSON parsing alone does not prove Desktop compatibility. State the exact validation level.
 
### 6. Review scope
 
Confirm only intended files changed, no mass churn occurred, IDs/references are stable, theme JSON is valid, design source is traceable, and no model/DAX artifacts changed unintentionally.
 
## Stop and escalate when
 
- PBIR source is absent/incompatible
- requested design requires DAX/model changes
- a schema field is unknown
- readable design direction is unavailable
- Desktop validation is required but unavailable
- safe implementation requires broad regeneration
- approved sources conflict
 
## Completion criteria
 
- approved specification was followed
- edits stay in owned paths
- diff is narrow and reviewable
- available deterministic checks passed
- unsupported validation is disclosed
- no schema/semantics were invented
- no sensitive/environment-specific information was introduced
 
## Required output
 
### Status
 
Completed | Blocked | Needs decision
 
### Files changed
 
List exact repository-relative paths and purpose.
 
### Requirements implemented
 
Trace each change to the approved design requirement.
 
### Validation
 
List check, result, evidence, and unavailable manual validation.
 
### Diff summary
 
State scope, identifiers changed, and confirmation of no unrelated churn.
 
### Limitations
 
List unsupported checks or environment constraints.
 
### Handoff
 
Provide artifacts/evidence to `bi-auditor` and `pr-reviewer`.
