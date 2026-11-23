---
name: dimensional-modeling
description: >
  Designs and reviews Power BI dimensional models including analytical
  processes, fact grain, fact types, dimensions, conformed dimensions, date
  architecture, bridges, keys, relationships, cardinality, filter direction,
  and semantic-model boundaries.
---
 
# Power BI Dimensional Modeling
 
## Purpose
 
Design semantic models that are analytically correct, understandable,
performant, maintainable, extensible, and predictable under filter context.
 
The semantic model is an analytical product, not a direct copy of an
operational source schema.
 
## Workflow
 
### 1. Identify the Business Process
 
Identify the analytical process, such as orders, invoice lines, incidents,
service requests, SLA measurements, inventory snapshots, or headcount
snapshots. Separate processes when their grains differ.
 
### 2. Declare Grain
 
Every fact must state:
 
> One row represents...
 
Never approve an ambiguous or mixed grain.
 
### 3. Classify the Fact
 
Classify each fact as:
 
- transaction fact
- periodic snapshot
- accumulating snapshot
- factless fact
 
Document why the type fits the process.
 
### 4. Identify Facts
 
Define foreign keys, transaction identifiers, event dates, numeric facts, and
additive, semi-additive, or non-additive behavior. Do not expose raw numeric
columns as metrics when default aggregation would mislead users.
 
### 5. Identify Dimensions
 
Dimensions describe stable business concepts such as Date, Customer, Product,
Service, Market, Location, Employee, Supplier, and Status. Avoid duplicating
the same concept across facts without justification.
 
### 6. Identify Conformed Dimensions
 
Use conformed dimensions when their meaning is consistent across business
processes. Do not label a dimension conformed when different processes use
materially different definitions.
 
### 7. Design Relationships
 
For every relationship document:
 
- from table and column
- to table and column
- cardinality
- filter direction
- active or inactive status
- business rationale
 
Default to Dimension 1 -> * Fact, one-to-many, single-direction, and active.
 
### 8. Design Date Architecture
 
Normally use an explicit Date dimension containing calendar and, where
required, fiscal attributes, sort keys, weeks, and working-day indicators.
Use role-playing dates when a fact has multiple meaningful date roles.
 
### 9. Review Model Boundaries
 
Every included table must support a defined KPI, dimension, relationship,
security rule, or documented requirement. Source availability alone is not a
reason to include a table.
 
## Relationship Exceptions
 
### Bidirectional Relationships
 
Treat as exceptions. Confirm the requirement, alternatives, ambiguity risk,
and future-extension impact before approval.
 
### Many-to-Many Relationships
 
Investigate duplicated keys first. Prefer a governed bridge when it more
clearly represents the business structure. Define bridge grain and uniqueness.
 
### Fact-to-Fact Relationships
 
Avoid direct fact-to-fact relationships. Prefer conformed dimensions.
 
### Snowflake Dimensions
 
Do not reproduce source normalization automatically. Use snowflaking only for
a clear semantic, governance, ownership, or scale benefit.
 
## Keys
 
Distinguish source keys, business keys, surrogate keys, and composite keys. Do
not assume source uniqueness without evidence.
 
## Degenerate Dimensions
 
Keep analytically valuable transaction identifiers such as Order Number or
Ticket Number in the fact when a separate descriptive dimension has no value.
 
## Required Output
 
### Business Processes
 
List each analytical process.
 
### Fact Design
 
| Fact | Grain | Type | Source | Purpose |
|---|---|---|---|---|
 
### Dimension Design
 
| Dimension | Business Concept | Key | Conformed | Purpose |
|---|---|---|---|---|
 
### Relationship Design
 
| From | Column | To | Column | Cardinality | Direction | Active | Rationale |
|---|---|---|---|---|---|---|---|
 
### Architecture Exceptions
 
List every many-to-many, bidirectional, bridge, inactive, snowflake, or
fact-to-fact exception.
 
### Data-Modeler Handoff
 
Provide approved grains, fact types, keys, relationships, date strategy,
required source fields, and unresolved data-quality risks.
 
## Validation Checklist
 
- Every fact has explicit grain.
- Processes with different grains are separated.
- Fact types and additivity are understood.
- Dimensions represent business concepts.
- Conformed and role-playing dimensions are identified.
- Date architecture is defined.
- Cardinalities and filter directions are documented.
- Exceptions and bridge grains are justified.
- Model boundaries are intentional.
- The design supports required KPIs and security.
 
Return `DIMENSIONAL MODEL STATUS: BLOCKED` when material issues remain.
