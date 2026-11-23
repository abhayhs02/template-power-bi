---
name: kpi-semantic-design
description: >
  Defines implementation-ready Power BI KPI contracts covering business
  meaning, populations, formulas, aggregation, time behavior, targets,
  thresholds, dimensional behavior, dependencies, source authority, and edge
  cases before DAX implementation.
---
 
# Power BI KPI Semantic Design
 
## Purpose
 
Convert business metrics into implementation-ready KPI contracts. The BI
Architect defines meaning; the DAX Engineer implements the approved meaning.
 
## Required KPI Contract
 
Every material KPI must define:
 
- name
- business question
- business definition
- logical formula
- numerator and denominator where applicable
- qualifying and excluded populations
- aggregation behavior
- time behavior
- target and thresholds
- dimensions
- edge cases
- authoritative source
- business owner when provided
- dependencies
- readiness status
 
## Workflow
 
### 1. Name the KPI
 
Use a precise business-readable name, such as `SLA Compliance %` rather than
`SLA %`.
 
### 2. Define the Business Question
 
State what decision the KPI supports.
 
### 3. Define Business Meaning
 
Describe the meaning without DAX syntax.
 
### 4. Define the Logical Formula
 
Express the business calculation independently of implementation language.
 
### 5. Define Populations
 
Clarify qualifying, excluded, cancelled, duplicate, missing, and not-applicable
records, and the grain at which records are counted.
 
### 6. Define Aggregation
 
Classify as sum, count, distinct count, average, weighted average, ratio,
snapshot, semi-additive, or custom. Ratios should normally be recalculated
from components in the current filter context rather than summed.
 
### 7. Define Time Behavior
 
Specify point-in-time, MTD, QTD, YTD, prior period, prior year, rolling period,
fiscal period, snapshot, or trailing behavior. Define incomplete-period rules.
 
### 8. Define Targets and Thresholds
 
Targets may be fixed, contractual, period-specific, customer-specific,
service-specific, or dynamically sourced. Do not invent targets or threshold
boundaries.
 
### 9. Define Dimensional Behavior
 
List every dimension through which the KPI must behave correctly, such as Date,
Market, Customer, Service, Product, Contract, or Service Tower.
 
### 10. Define Edge Cases
 
Explicitly define the intended result for zero denominators, missing values,
partial periods, late-arriving data, duplicates, cancellations, future dates,
unavailable targets, and not-applicable results.
 
### 11. Identify Dependencies
 
Separate reusable base measures from derived metrics. Prefer shared metric
dependency chains over duplicated business logic.
 
### 12. Identify Source Authority
 
Record the authoritative source. Escalate disagreements rather than selecting a
source based on convenience.
 
## KPI Contract Template
 
### KPI: [Name]
 
- Business Question: [question]
- Business Definition: [definition]
- Logical Formula: [formula]
- Numerator: [definition or not applicable]
- Denominator: [definition or not applicable]
- Population Rules: [rules]
- Aggregation: [behavior]
- Time Behavior: [behavior]
- Target: [value, source, or unresolved]
- Thresholds: [rules, source, or unresolved]
- Dimensions: [list]
- Edge Cases: [list]
- Authoritative Source: [source]
- Business Owner: [known owner or unresolved]
- Dependencies: [base and derived metrics]
- Status: READY or BLOCKED
 
## DAX-Engineer Handoff
 
Provide the approved contract, required base and derived measures, populations,
time behavior, target and threshold sources, formatting expectation, edge-case
outcomes, and expected tests. Do not prescribe DAX unless a specific semantic
behavior requires an implementation constraint.
 
## Validation Checklist
 
- Name, question, definition, and logical formula are clear.
- Populations and aggregation are defined.
- Time behavior is defined.
- Targets and thresholds are sourced, not invented.
- Dimensions and dependencies are identified.
- Zero denominator, missing value, duplicate, and partial-period behavior are
  defined.
- Source authority is known.
 
Return `KPI STATUS: BLOCKED` when material semantics remain unresolved.
