---
name: dax-measure-engineering
description: Implements approved KPI and analytical definitions as maintainable Power BI DAX measures, calculation groups, calculation items, time-intelligence logic, and format-string expressions. Use for every new or materially changed DAX artifact. Requires approved semantics and model dependencies. Does not authorize KPI, model, Power Query, RLS, PBIR, or theme changes.
---

# DAX Measure Engineering

## Purpose
Provide a repeatable method for translating approved business semantics into correct, maintainable, testable DAX.

## Primary consumer
- `dax-engineer`

## Supporting consumers
- `bi-auditor`: inspect quality and evidence without implementing fixes.
- `pr-reviewer`: review compliance without modifying DAX.

## Required inputs
- approved KPI or analytical definition
- approved grain
- numerator/denominator and aggregation behavior
- filters and exclusions
- target, threshold, directionality, and applicable status logic
- time behavior
- blank/zero/not-applicable behavior
- required tables, columns, relationships, hierarchies, and date table
- naming, display-folder, description, and format conventions
- expected examples or reconciliation source

## Preconditions
Do not implement when:
- KPI semantics are incomplete
- model dependencies are absent
- grain conflicts with the semantic model
- total/subtotal behavior is materially undefined
- security behavior is unclear

Return the gap to `bi-orchestrator` rather than inventing it.

## Procedure

### 1. Map semantics
Create an implementation mapping:
- approved definition → DAX behavior
- approved grain → expected filter context
- exclusions → explicit filter behavior
- time rule → date-table behavior
- directionality/target → status behavior
- blank/zero/not-applicable → result behavior

### 2. Inspect existing DAX
Search for:
- existing base measures
- equivalent or overlapping measures
- naming conventions
- display folders
- descriptions
- calculation groups
- dynamic format strings
- measure dependency patterns

Prefer reuse when semantics are identical. Do not reuse merely because names are similar.

### 3. Choose measure architecture
Prefer a clear structure such as:
- base aggregation measure
- reusable intermediate measure only when it has independent meaning or genuine reuse
- final KPI/presentation measure
- separate target/variance/status measures when approved and useful

Avoid excessive measure branching that makes dependency chains difficult to understand.

### 4. Implement safely
Apply applicable conventions:
- variables for repeated expressions and readable intermediate intent
- safe division
- explicit filter behavior
- approved date table for time intelligence
- explicit handling of totals for non-additive measures
- numeric format strings rather than text conversion
- clear names, descriptions, folders, and metadata

### 5. Calculation groups
When approved:
- identify affected measure set
- define calculation items
- define precedence
- define format-string behavior
- test totals, percentages, currencies, time calculations, and interaction with other calculation groups

### 6. Validate scenarios
Test applicable cases:
- expected normal result
- no rows
- blank source
- zero denominator
- not applicable
- missing target
- one filter
- multiple filters
- total and subtotal
- first/last period boundary
- drill-down and cross-filter context

Use approved examples, source reconciliation, or manually derived expected results.

### 7. Validate source changes
Confirm:
- DAX/TMDL parses at the available validation level
- only intended artifacts changed
- no model/PBIR/theme/security change occurred
- metadata and formats are correct
- no hardcoded sensitive or environment-specific values exist

## Quality rules
- Correctness against approved semantics is more important than brevity.
- Readability is more important than cleverness.
- Avoid implicit measures for governed calculations.
- Avoid `FORMAT` when numeric behavior must be preserved.
- Use broad filter removal only when explicitly required.
- Do not hide model defects with complex DAX.
- Do not duplicate already approved logic.
- Treat non-additive totals deliberately.
- Preserve numeric type and usable sorting/filtering behavior.

## Completion criteria
- semantic mapping is documented
- required dependencies exist
- DAX is readable and scoped
- edge and total scenarios are tested
- expected and actual results are recorded
- format and metadata follow repository conventions
- source validation and diff review are complete
- performance-analysis requirement is identified

## Required output

### Status
Completed | Blocked | Needs decision

### Semantic mapping
- approved source
- implemented behavior

### Artifacts changed
For each changed artifact record:
- exact repository-relative path
- measure, calculation-group, calculation-item, or format-string name
- change type: added | modified | removed
- approved KPI/analytical definition implemented
- reason for the change

### Validation scenarios and results
For each applicable scenario record:
- scenario name
- filter/context applied
- expected result
- actual result
- pass/fail
- evidence or reconciliation source

Include relevant cases such as:
- normal result
- blank source
- zero denominator
- not applicable
- missing target
- single and multiple filters
- total/subtotal context
- time-period boundaries
- drill/cross-filter context

Do not mark validation passed when the expected result is unknown.

### Metadata and formatting
Confirm:
- measure naming follows repository conventions
- display folders are correct
- descriptions are present where required
- numeric type is preserved
- static or dynamic format strings match approved semantics
- percentage, currency, decimal, and unit formatting are correct
- no inappropriate use of `FORMAT` converts governed numeric results to text
- calculation-group metadata and precedence are correct when applicable

Record any intentional deviation.

### Performance-analysis trigger
Required | Not required

If required:
- state the trigger
- invoke `dax-performance-analysis`
- include its evidence in the handoff

Typical triggers:
- slow existing measure
- performance acceptance criteria
- iterators over large rowsets
- complex virtual tables
- high-cardinality filtering
- repeated expensive expressions
- calculation-group overhead
- auditor/reviewer performance finding

If not required:
- give one concise reason.

### Risks and dependencies
Record:
- unresolved KPI-semantic questions
- missing or questionable model dependencies
- total/subtotal risks
- filter-context assumptions
- calculation-group interaction risks
- performance concerns
- validation limitations
- security/RLS implications, if any

For each dependency state:
- affected artifact
- impact
- owning agent
- required follow-up

Route work outside DAX ownership through `bi-orchestrator`. Do not repair model or architecture problems inside DAX.

### Handoff evidence
Provide:
- approved KPI/analytical definition used
- exact files changed
- measures/calculation groups affected
- semantic mapping
- validation scenarios and results
- reconciliation evidence
- metadata/formatting confirmation
- performance-analysis status and evidence
- Git diff summary
- unresolved risks and dependencies
- validation limitations

This package must provide enough evidence for `bi-auditor` to verify the implementation and `pr-reviewer` to perform an independent review.
