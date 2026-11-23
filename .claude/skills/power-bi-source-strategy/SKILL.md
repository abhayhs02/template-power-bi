---
name: power-bi-source-strategy
description: >
  Defines Power BI source authority, ingestion, storage mode, refresh,
  incremental refresh, history, late-arriving data, gateway, query folding,
  parameterization, portability, source load, and failure architecture.
---
 
# Power BI Source and Refresh Strategy
 
## Purpose
 
Define how data reaches and refreshes the semantic model. Storage and refresh
choices must follow business freshness, source capability, scale, security, and
operational constraints, not dataset size alone.
 
## Required Inputs
 
Determine source systems and technologies, authority, keys, volume, growth,
history, freshness, refresh frequency and window, source availability, gateway,
security, target environment, concurrency, and known quality issues.
 
## Workflow
 
### 1. Establish Source Authority
 
For each subject, identify the authoritative system, available history, keys,
update behavior, owner when known, and quality concerns. Do not combine
conflicting sources without a reconciliation rule.
 
### 2. Define Freshness
 
Translate vague requests into measurable latency, such as previous business
day, hourly, every 30 minutes, or monthly close.
 
### 3. Evaluate Import
 
Prefer Import when it satisfies the requirement. Evaluate model size, refresh
time, frequency, concurrency, history, capacity, and latency.
 
### 4. Evaluate DirectQuery
 
DirectQuery requires explicit justification, such as unavoidable freshness,
governance restrictions, or a source designed for analytical queries. Assess
source speed, network latency, folding, concurrency, gateway, source workload,
model limitations, DAX limitations, and report interactions.
 
Do not choose DirectQuery merely because data is large.
 
### 5. Evaluate Composite Models
 
Document table modes, rationale, relationship, security, performance, and
refresh impacts. Accept complexity only for a clear business benefit.
 
### 6. Define History
 
Specify required retained history. Do not load unlimited history without a
business requirement.
 
### 7. Evaluate Incremental Refresh
 
Define archive period, refresh period, date column, late-arriving correction
window, partition expectation, and folding requirement.
 
### 8. Handle Late-Arriving Data
 
Define how invoice corrections, incident changes, delayed SLA measurements,
or finance adjustments affect historical refresh ranges.
 
### 9. Define Gateway Dependency
 
Document source type, gateway need, enterprise connection, ownership, and
operational dependency. Never store gateway credentials in Git.
 
### 10. Define Parameters
 
Use environment-neutral parameters for server, database, environment,
SharePoint root, storage path, or API base URL. Never embed credentials.
 
### 11. Evaluate Query Folding
 
Flag transformations likely to break folding, cause full extraction, increase
refresh duration, or overload the source. M implementation belongs to the Data
Modeler.
 
### 12. Define Failure Handling
 
Consider source unavailability, schema drift, gateway failure, credential
expiry, timeout, malformed data, partial refresh, and cancellation. Define
monitoring and notification expectations.
 
## Personal Environment Boundary
 
Personal repositories may hold schemas, generic connection definitions,
synthetic or permitted anonymized data, metadata, and validations. They must not
hold company data, production extracts, secrets, gateway credentials, tokens,
passwords, or restricted tenant material.
 
## Required Output
 
### Source Inventory
 
| Subject | Authoritative Source | Technology | Key | History | Concern |
|---|---|---|---|---|---|
 
### Storage Decision
 
| Table or Subject | Mode | Rationale | Risk |
|---|---|---|---|
 
### Refresh Design
 
Document freshness, frequency, history, incremental refresh, correction window,
gateway, parameters, source load, and failure behavior.
 
### Data-Modeler Handoff
 
Provide source mappings, required columns, keys, filtering and folding
expectations, parameters, refresh requirements, and known quality risks.
 
## Validation Checklist
 
- Sources and authority are identified.
- Volume, growth, freshness, frequency, and history are defined.
- Storage mode is justified.
- Incremental refresh, late changes, folding, gateway, parameters, source load,
  and failures are considered.
- Credentials are excluded.
- Personal development uses safe data only.
 
Return `SOURCE STRATEGY STATUS: BLOCKED` when critical information is missing.
