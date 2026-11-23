
---
name: power-bi-performance-architecture
description: >
  Defines Power BI model and report performance architecture including scale,
  growth, cardinality, VertiPaq efficiency, relationships, storage modes,
  partitions, aggregations, DAX risks, visual query load, concurrency, refresh
  performance, evidence, and measurable acceptance targets.
---
 
# Power BI Performance Architecture
 
## Purpose
 
Identify architectural decisions affecting model size, refresh duration, query
response, report interaction, source load, concurrency, maintainability, and
capacity. This skill defines risks and constraints; it does not implement DAX,
TMDL, M, or PBIR.
 
## Evaluation Order
 
Review performance in this order:
 
1. business requirement
2. data volume and growth
3. model grain
4. table boundaries
5. column cardinality
6. relationship architecture
7. storage mode
8. partitions and aggregations
9. DAX complexity
10. report query patterns
 
Do not rely on late DAX rewrites to repair a poor model.
 
## Required Inputs
 
Collect fact row volume, growth, history, dimensions, high-cardinality fields,
concurrency, refresh schedule and window, source limits, interactions, target
capacity constraints when known, and response expectations.
 
## Workflow
 
### 1. Evaluate Grain and Volume
 
Preserve required detail, but do not retain unnecessary detail merely because
the source provides it. Document current and future volume, history, and drill
detail requirements.
 
### 2. Evaluate Column Necessity
 
Identify columns needed for relationships, filtering, display, and calculations,
and flag undocumented columns. Every imported column has a cost.
 
### 3. Evaluate Cardinality
 
Review IDs, GUIDs, timestamps, long text, URLs, comments, and highly precise
decimals. Determine whether each is analytically necessary.
 
### 4. Evaluate Data Types and Precision
 
Flag unnecessary decimal or datetime precision, text that belongs in a
dimension, identifiers treated as facts, and source types wider than needed.
Implementation belongs to the Data Modeler.
 
### 5. Evaluate Relationship Complexity
 
Review many-to-many, bidirectional filters, ambiguous paths, fact-to-fact joins,
large bridges, and high-cardinality text relationships. Recommend cleaner model
architecture first.
 
### 6. Evaluate Storage Mode
 
Coordinate with `power-bi-source-strategy`. For DirectQuery consider source
response, network, concurrency, gateway overhead, visual query count, and source
workload.
 
### 7. Evaluate Partitions and Incremental Refresh
 
Define archive and refresh periods, correction window, partition key, expected
partition count, folding, and refresh benefit.
 
### 8. Evaluate Aggregations
 
Consider aggregation tables when detailed facts are large and common queries use
higher grains. Define aggregation grain, dimensions, metrics, detail fallback,
and refresh alignment.
 
### 9. Evaluate DAX Risk
 
Flag large-table iterators, repeated context transitions, broad FILTER usage,
virtual relationships, dynamic segmentation, nested branching, repeated logic,
expensive distinct counts, and complex semi-additive calculations. Detailed
optimization belongs to the DAX Engineer.
 
### 10. Evaluate Report Query Load
 
Flag excessive visuals, high-cardinality slicers, large detail tables,
unnecessary cross-highlighting, expensive custom visuals, simultaneous queries,
broad default history, and costly drill-through. Implementation belongs to the
Visual Designer.
 
### 11. Define Measurable Targets
 
Where approved requirements exist, record interaction response, refresh window,
model-size, concurrency, source-query, and capacity expectations. Do not invent
targets; mark missing acceptance criteria unresolved.
 
### 12. Define Validation Evidence
 
Recommend compatible tools such as DAX Studio server timings and query plans,
VertiPaq Analyzer statistics, Tabular Editor Best Practice Analyzer, Power BI
Performance Analyzer, refresh logs, source query plans, and CI metadata rules.
Tool results are evidence, not substitutes for judgment.
 
## Risk Levels
 
- Critical: likely to prevent acceptable or correct operation.
- High: likely to create major model, refresh, or interaction problems.
- Medium: material concern requiring monitoring or optimization.
- Low: limited-risk improvement opportunity.
 
## Required Output
 
### Performance Context
 
Describe scale, growth, freshness, concurrency, and interactions.
 
### Architectural Risks
 
| Risk | Area | Severity | Evidence | Recommendation |
|---|---|---|---|---|
 
### Recommendations
 
Include grain, table boundaries, cardinality, relationships, storage, partitions,
aggregations, DAX risks, report query load, and measurable targets.
 
### Downstream Handoffs
 
- Data Modeler: column reduction, types, partitions, relationships, and folding.
- DAX Engineer: expensive semantics, tests, base measures, and evidence.
- Visual Designer: visual-count, slicer, default-page, and test constraints.
- BI Auditor: exceptions, BPA checks, model-size, and validation requirements.
 
## Validation Checklist
 
- Volume, growth, history, grain, columns, and cardinality are reviewed.
- Data types, relationships, storage, partitions, and aggregations are reviewed.
- DAX and report-query risks are identified.
- Targets are recorded or explicitly unresolved.
- Validation tools and required evidence are identified.
 
Return `PERFORMANCE ARCHITECTURE STATUS: BLOCKED` when viability cannot be
established.
