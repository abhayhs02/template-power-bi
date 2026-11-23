
---
name: rls-security-design
description: >
  Designs Power BI row-level security including protected scope, secured
  entities, security grain, authenticated identity, authorization mappings,
  static and dynamic RLS, hierarchy, privileged access, filter propagation,
  default-deny behavior, and positive and negative test personas.
---
 
# Power BI RLS and Security Design
 
## Purpose
 
Design governed data visibility restrictions. RLS is security architecture,
not merely a DAX expression.
 
## Required Inputs
 
Determine protected data, secured entity, user population, authenticated
identity, mapping source, hierarchy, privileged access, default behavior,
target tenant, and required negative tests. Do not invent security rules.
 
## Workflow
 
### 1. Identify Protected Scope
 
Identify the entity controlling access, such as Market, Customer, Region,
Department, Legal Entity, Business Unit, Service, or Contract.
 
### 2. Define Security Grain
 
State `One row represents...`, such as one user authorized for one market.
Security mappings require explicit grain.
 
### 3. Define Identity
 
Use an approved enterprise identity such as user principal name or another
stable governed identity. Do not store real enterprise identity lists in the
personal repository.
 
### 4. Define Authorization Source
 
Identify a governed database, Dataverse table, SharePoint list, identity
system, or other approved source. Avoid embedding large maintenance lists in
report source files.
 
### 5. Select Static or Dynamic RLS
 
Use static roles for limited stable groups. Use dynamic RLS when authorization
depends on the authenticated user. Avoid large numbers of static roles for
dynamic populations.
 
### 6. Define Multi-Entity Access
 
Support users authorized for multiple entities without creating ambiguous
filter paths.
 
### 7. Define Hierarchical Access
 
Document hierarchy source, parent-child logic, effective dates, inheritance,
exceptions, and change behavior. Do not assume reporting hierarchy equals data
access hierarchy.
 
### 8. Define Default Behavior
 
Prefer default deny: a user without a valid mapping sees no restricted rows.
Broad-access exceptions require explicit approval.
 
### 9. Define Privileged Access
 
Identify administrators, executives, controllers, auditors, or global owners.
Document whether access is implemented through semantic-model security,
workspace permissions, or a separate governed model.
 
### 10. Review Filter Propagation
 
Evaluate relationships, bridges, many-to-many paths, inactive relationships,
bidirectional filtering, and multiple security dimensions. Avoid bidirectional
security unless justified and tested.
 
### 11. Separate RLS From Object Security
 
If tables or columns must be hidden, evaluate object-level security, separate
models, or another governed boundary. Do not misuse RLS for object visibility.
 
### 12. Define Test Personas
 
Create synthetic personas for single-entity, multi-entity, hierarchical,
privileged, and unauthorized users.
 
### 13. Define Negative Tests
 
Test unauthorized entities, missing and duplicate mappings, multiple mappings,
hierarchy changes, inactive users where relevant, and privileged accounts.
Positive tests alone are insufficient.
 
## Personal Repository Rules
 
Personal repositories may contain security schemas, synthetic identities,
synthetic mappings, and test personas. They must not contain real employees,
real access lists, confidential mappings, authentication material, tokens, or
tenant credentials.
 
## Required Output
 
Document protected scope, secured entity, security grain, identity,
authorization source, RLS strategy, filter path, hierarchy, privileged access,
default behavior, test personas, and unresolved questions.
 
### Data-Modeler Handoff
 
Provide security tables, grain, columns, relationships, filter direction, RLS
behavior, and synthetic test-data requirements.
 
## Validation Checklist
 
- Protected data, secured entity, grain, identity, and source are defined.
- Static/dynamic approach is selected.
- Multi-entity and hierarchical access are considered.
- Default deny and privileged access are defined.
- Filter path and bidirectional risks are reviewed.
- Positive and negative tests are defined.
- Real identity mappings are excluded from personal Git.
 
Return `SECURITY ARCHITECTURE STATUS: BLOCKED` when material decisions remain.
