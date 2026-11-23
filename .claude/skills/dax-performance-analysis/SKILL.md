---
name: dax-performance-analysis
description: Evaluates and improves DAX performance using available execution evidence, query plans, server timings, model context, and static review. Use for slow measures, complex iterators or virtual tables, large-model/high-cardinality scenarios, audit findings, or explicit performance acceptance criteria. Does not authorize semantic changes or model redesign.
---

# DAX Performance Analysis

## Purpose
Identify DAX performance risks, measure actual behavior when tooling is available, propose bounded optimizations, and verify that optimization preserves approved semantics.

## Primary consumer
- `dax-engineer`

## Supporting consumers
- `bi-auditor`: independent quality assessment.
- `pr-reviewer`: evaluate evidence and unresolved risk.
- `bi-architect`: consume findings when architecture may require revision; architecture changes remain the architect's authority.

## Triggers
Use this skill when any applies:
- report or measure is slow
- performance is an acceptance criterion
- large fact tables or high-cardinality filters are involved
- DAX introduces iterators over large rowsets
- complex virtual tables or nested filter manipulation are used
- repeated expensive expressions exist
- calculation groups create noticeable overhead
- audit/reviewer requests performance evidence
- a change affects frequently used executive/report interactions

## Required inputs
- target measure/query and dependencies
- approved semantic behavior and validation scenarios
- model size/cardinality context when available
- test filter context and representative report interaction
- baseline evidence when available
- available tools such as DAX Studio, Performance Analyzer, server timings, query plan, Tabular Editor, or repository scripts

## Evidence levels
Classify findings accurately:

### Level 1: Measured
Actual timings/server timings/query-plan evidence captured under representative conditions.

### Level 2: Comparative
Before/after execution evidence exists, but tooling or environment does not provide full engine detail.

### Level 3: Static risk review
Only source/model inspection is possible. Report risks as risks, not measured bottlenecks.

### Level 4: Unavailable
Required tooling, model, or data is unavailable. Do not claim performance success.

## Procedure

### 1. Establish baseline
Record:
- measure/query
- representative filter context
- report interaction or query used
- environment and data state
- timing/evidence method
- repeat count when applicable

Avoid comparing timings from materially different data, filters, caches, or environments without stating the limitation.

### 2. Inspect dependency chain
Review:
- base measures
- repeated branches
- nested iterators
- filter-context transitions
- virtual tables
- relationship-dependent logic
- calculation-group interactions
- high-cardinality groupings

### 3. Identify risk patterns
Check for applicable risks:
- iterating a large fact table when a smaller grouped table would preserve semantics
- repeated evaluation of the same expensive expression
- broad `FILTER` over large tables
- unnecessary `ALL`, `REMOVEFILTERS`, or context reconstruction
- excessive measure dependency depth
- expensive string operations
- unnecessary materialization of virtual tables
- misuse of calculated columns/measures
- non-selective filters
- complex totals recalculated at high grain
- calculation-group interactions multiplying work

A pattern is not automatically a defect. Tie findings to evidence and approved semantics.

### 4. Form an optimization hypothesis
For each candidate change state:
- observed evidence or static risk
- expected engine/logic effect
- semantic invariant that must remain unchanged
- validation needed

### 5. Implement within authority
The DAX Engineer may modify only approved DAX-owned artifacts.

If optimization requires:
- relationship change
- aggregation table
- new column
- different grain
- partition/storage-mode/source change
- KPI semantic change

stop and route it through `bi-orchestrator` to the appropriate owner.

### 6. Revalidate correctness
Run the same semantic scenarios used for the original measure, including totals and edge cases.

Performance improvement is invalid if approved results change.

### 7. Compare performance
When measurement is available:
- use comparable conditions
- capture before and after
- report absolute and relative difference
- note cache/environment limitations
- avoid claiming general improvement from one unrepresentative query

### 8. Report remaining risk
State:
- unresolved bottlenecks
- model/architecture dependencies
- unavailable evidence
- expected production-scale uncertainty

## Optimization principles
- Preserve semantics first.
- Measure before claiming improvement when tools are available.
- Prefer reducing repeated work and unnecessary row iteration.
- Prefer clear reusable measures over opaque micro-optimizations.
- Do not trade maintainability for negligible unmeasured gain.
- Do not shift a model-design defect into DAX.
- Do not use performance claims to justify an unapproved semantic change.

## Stop and escalate when
- representative data/model is unavailable and measurement is mandatory
- required optimization crosses DAX ownership
- before/after results differ semantically
- calculation-group or total behavior becomes ambiguous
- security/RLS context might change behavior
- performance targets are undefined but required for acceptance

## Completion criteria
- evidence level is declared
- baseline or static risk is documented
- optimization hypothesis is explicit
- semantic validation passed
- before/after evidence is captured when available
- limitations and remaining risk are stated
- architecture/model dependencies are routed rather than implemented

## Required output

### Status
Completed | Blocked | Needs decision

### Evidence level
Measured | Comparative | Static risk review | Unavailable

### Baseline
- measure/query
- context
- method/tool
- result

### Findings
For each:
- evidence or risk pattern
- impact
- affected artifact

### Optimization performed
- exact change
- semantic invariant

### Correctness revalidation
- scenarios and results

### Performance comparison
- before: baseline timing, query-plan/server-timing evidence, or static-risk state
- after: post-optimization result using comparable conditions
- relative change: absolute and percentage improvement/regression when measurable
- semantic equivalence: confirm approved results remained unchanged
- limitations: cache state, environment differences, representative-data limitations, unavailable tooling, or other factors affecting comparison

### Remaining risks and routed dependencies
For every unresolved issue record:
- risk or limitation
- expected impact
- whether it is measured or inferred
- affected measure/query/artifact
- owning agent
- required follow-up

Route dependencies outside DAX ownership through `bi-orchestrator`.

Examples:
- relationship/model redesign → `data-modeler` or `bi-architect`
- grain/source/storage-mode decision → `bi-architect`
- report interaction causing workload concerns → `visual-designer`
- independent validation concern → `bi-auditor`

Do not resolve another agent's responsibility inside this skill.

### Handoff evidence
Provide:
- measures/queries analyzed
- exact files changed
- evidence level used
- baseline evidence
- optimization performed
- correctness revalidation results
- before/after performance evidence when measurable
- Git diff summary
- validation limitations
- unresolved risks
- routed dependencies

This evidence must be sufficient for `bi-auditor` to validate the change and for `pr-reviewer` to independently assess the performance claim.