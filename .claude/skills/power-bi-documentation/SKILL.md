---
name: power-bi-documentation
description: Creates and updates evidence-based Power BI repository documentation, including README, architecture summaries, KPI catalogues, data dictionaries, report-page guides, refresh and RLS guidance, user/admin instructions, release notes, known limitations, and handover material. Use at approved milestones or when a Power BI change has documentation impact. Never infer business definitions from implementation alone.
---
 
# Power BI Documentation
 
## Purpose
 
Create documentation that accurately reflects approved Power BI decisions and artifacts and is usable by developers, administrators, analysts, and report consumers.
 
## Primary consumer
 
- `doc-writer`
 
## Supporting consumer
 
- `pr-reviewer`: verify completeness and consistency without rewriting documentation.
 
## Core rule
 
Implementation is evidence, not automatically business truth.
 
Do not infer KPI meaning, target, threshold, exclusion, ownership, or directionality from DAX alone. Use approved definitions. Escalate conflicts.
 
## Source precedence
 
1. Approved current user decision
2. Approved requirements and architecture
3. Approved KPI, source, and security artifacts
4. Accepted implementation and validation evidence
5. Existing documentation
 
Older documentation does not override newer approved decisions.
 
## Deliverable selection
 
Create only what the task/milestone requires:
 
- README/setup guide
- architecture overview
- semantic-model overview
- data dictionary
- KPI/measure catalogue
- report-page/navigation guide
- RLS/security guide
- source/refresh guide
- user guide
- administrator/operations guide
- release notes
- handover guide
- limitations/troubleshooting
 
## Workflow
 
### 1. Define audience and purpose
 
Identify readers, decision/task supported, lifecycle phase, required deliverable, and existing file to update.
 
### 2. Collect approved evidence
 
Read relevant requirements, architecture, KPIs, PBIP source, validation/audit/review evidence, design standards, and release details.
 
### 3. Navigate actual project source
 
Use `pbip-project-navigation` to verify object/file names rather than assuming paths.
 
### 4. Reconcile vocabulary
 
Use consistent names for business processes, facts/dimensions, KPIs/measures, pages/navigation, RLS personas, sources, refresh, and deployment.
 
### 5. Write for the target reader
 
- README: purpose, prerequisites, structure, setup, validation, useful links.
- KPI catalogue: question, definition, logical formula, grain, directionality, target/threshold, dimensions, edge cases, source, owner, measure.
- Data dictionary: object, business meaning, source, type, key/relationship role, format, visibility, notes.
- User guide: purpose, pages, filters, navigation, drill/tooltips, statuses, blank/no-data behavior, refresh timing.
- Operations/handover: prerequisites, source parameters, gateway, refresh, RLS, validation, publish process, limitations, rollback/recovery where known.
- Release notes: version, source commit, changes, breaking impact, migration, known issues, evidence.
 
### 6. Validate
 
Verify:
 
- relative links and paths
- source object names
- KPI definitions against approved catalogue
- page names against PBIR
- tables/measures against TMDL
- commands against scripts
- sensitive data absence
- validation/deployment claims against evidence
 
## Boundaries
 
- Do not change implementation or architecture.
- Do not invent business meaning or ownership.
- Do not claim unexecuted validation.
- Do not publish secrets or real identity mappings.
- Do not describe unreadable binary references as inspected.
- Do not create duplicate documents unnecessarily.
 
## Completion criteria
 
- audience/deliverable are clear
- content is grounded in approved sources
- terminology is consistent
- names/paths/commands are verified
- unknowns are visible
- sensitive values are absent
- documentation impact is complete but not overproduced
 
## Required output
 
### Status
 
Completed | Blocked | Needs decision
 
### Deliverable and audience
 
List target readers, purpose, milestone, and exact files.
 
### Sources used
 
List approved evidence and implementation artifacts.
 
### Documentation changes
 
Summarize exact additions/updates by file.
 
### Validation
 
Report links, paths, object names, commands, KPI definition checks, sensitive-data checks, and unsupported checks.
 
### Gaps and assumptions
 
List unresolved information, owner, and impact.
 
### Handoff
 
Return final documentation paths and next approval/review owner.
