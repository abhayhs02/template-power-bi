---
name: power-bi-visual-design
description: Defines implementation-ready design specifications for Power BI report pages using approved requirements, KPI definitions, design-taste.md, readable dashboard references, repository theme standards, and existing PBIR patterns. Use for page purpose, information hierarchy, visual selection, layout, typography, color, navigation, interactions, analytical states, and accessibility before PBIR editing.
---
 
# Power BI Visual Design
 
## Purpose
 
Create an approved, implementation-ready report design that answers business questions clearly and follows repository design policy.
 
## Primary consumer
 
- `visual-designer`
 
## Supporting consumers
 
- `pr-reviewer`: verify compliance without redesigning.
- `doc-writer`: describe accepted page behavior without changing it.
 
## Inputs
 
Use:
 
- governed design-material output
- approved report information architecture
- approved KPI catalogue
- current report source
- approved theme
- audience and acceptance criteria
 
## Workflow
 
### 1. Define the page job
 
State audience, business question, decision supported, KPI priority, dimensions, and expected consumption context.
 
### 2. Establish hierarchy
 
Define page identity, headline information, trends/comparisons, drivers/breakdowns, detail/exceptions, and controls.
 
### 3. Select visuals
 
Use the simplest visual fitting the analytical question. Document the visual's fields, purpose, rationale, sorting, target/reference, and role in the hierarchy.
 
Avoid decorative chart choice, unnecessary gauges, excessive pies/donuts, 3D visuals, and duplicate messages.
 
### 4. Specify layout
 
Define canvas/aspect ratio, grid, margins, sections, alignment, gaps, container/card rules, component sizing, and responsive/mobile behavior where required.
 
### 5. Specify style
 
Define typography, colors, semantic status, backgrounds, surfaces, borders, shadows, icon/image treatment, chart treatment, tables/matrices, and filters/navigation according to governed materials.
 
### 6. Specify interactions
 
Define cross-filtering, slicers, bookmarks, show/hide behavior, navigation, reset behavior, drill-through, tooltips, and back behavior.
 
### 7. Specify analytical states
 
Define normal, no-data, filtered-empty, blank, zero, not-applicable, unavailable target, incomplete period, stale-data, and error states where applicable.
 
### 8. Specify accessibility
 
Define contrast, type size, non-color cues, titles, labels, alt text, reading/tab order, accessible navigation, and color-vision-safe interpretation.
 
### 9. Identify dependencies
 
Route missing measures, fields, KPI definitions, architecture, security, or unsupported PBIR behavior to the owning agent.
 
### 10. Prepare PBIR handoff
 
Provide exact pages, expected files, placements, visuals, approved bindings, formatting, interactions, states, validation, and protected areas.
 
## Boundaries
 
This skill must not:
 
- invent or change KPI semantics
- create DAX/model/RLS logic
- ignore design-taste.md
- claim unreadable assets were inspected
- implement PBIR directly without using the editing skill
 
## Completion criteria
 
- design sources are explicit
- page purpose and audience are clear
- hierarchy and visuals answer approved questions
- layout/style are implementation-ready
- interactions and states are specified
- accessibility is specified
- dependencies are assigned
- PBIR handoff requires no invention
 
## Required output
 
### Status
 
Completed | Blocked | Needs decision
 
### Design sources
 
List governed design inputs.
 
### Page specification
 
Provide purpose, audience, questions, KPIs, hierarchy, visuals, layout, style, interactions, states, and accessibility.
 
### Dependencies
 
List issue, owner, resolution, and blocking status.
 
### PBIR handoff
 
Provide all implementation and validation details required by `pbir-report-editing`.
