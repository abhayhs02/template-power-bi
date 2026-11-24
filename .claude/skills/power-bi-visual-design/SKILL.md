---
name: power-bi-visual-design
description: Defines early design collaboration, implementation-ready Power BI page composition, visual technology selection across native visuals, Deneb, and HTML Content Lite, design-reference fidelity, and screenshot-based visual QA using docs/visual-qa/current/. Use during architecture for consultative design feasibility, after approved requirements for detailed design, before PBIR editing, and during controlled visual refinement. Does not define KPI semantics, modify DAX/model/RLS, implement PBIR directly, or claim visual QA without current screenshots.
---

# Power BI Visual Design

## Purpose
Collaborate early enough to shape usable report architecture, then create an approved implementation-ready design and evaluate the rendered dashboard through a controlled current-screenshot visual QA loop.

## Primary consumer
- `visual-designer`

## Supporting consumers
- `bi-architect`: consume consultative early design feasibility and page information-architecture advice.
- `pr-reviewer`: verify compliance without redesigning.
- `doc-writer`: describe accepted pages without changing design decisions.

## Authority boundary
This skill may:
- provide consultative design input during architecture
- define page purpose, analytical journey, hierarchy, and composition
- select native, Deneb, or HTML Content Lite approaches
- define approximate region/visual bounds
- define interactions, states, and accessibility
- compare designs with approved references
- review current rendered screenshots
- produce bounded visual-refinement findings

This skill must not:
- approve architecture
- invent KPI semantics
- create DAX/model/RLS/source logic
- implement PBIR directly
- assume custom-visual tenant approval
- push Git changes
- claim screenshot QA without readable current screenshots

## Required inputs
Use applicable:
- governed design-material output
- `StartYourProject.txt`
- approved report information architecture
- approved KPI catalogue
- current PBIP/PBIR source
- approved theme
- canvas and scrolling requirements
- audience and acceptance criteria
- accepted page precedents
- current screenshots under `docs/visual-qa/current/` for QA work

## Design-reference semantics

### Inspiration reference
A file containing `example` in its filename, such as `example_dashboard_design.png` or `example_dashboard_design.pptx`, is inspiration.

Extract principles and patterns, then adapt them to approved requirements and Power BI capabilities.

### Target replication reference
A file without `example`, such as `dashboard_design.png`, `dashboard-design.pptx`, or `dashboard_design.fig`, is a target design.

Replicate it as closely as practical while preserving correct analytics, accessibility, supported PBIR behavior, and approved canvas constraints.

Document material deviations.

## Workflow

### 1. Early Design Collaboration
When invoked during architecture:
- understand the proposed audience, questions, KPIs, dimensions, canvas, and navigation needs
- propose a preliminary analytical journey and page grouping
- identify dominant and supporting analysis
- identify visual/interactivity dependencies
- identify native, Deneb, and HTML Content Lite candidates
- identify model/DAX capabilities needed by the intended design
- identify overcrowding, feasibility, accessibility, or no-scroll risks
- return consultative advice to `bi-architect` through `bi-orchestrator`

Do not implement PBIR or turn preliminary advice into approved architecture.

### 2. Define page job
State:
- audience
- business question
- decision supported
- KPI priority
- dimensions
- consumption context
- expected user outcome

### 3. Define canvas and composition
Specify:
- canvas width/height/aspect
- scrolling behavior
- margins and usable bounds
- header/navigation
- KPI region
- dominant analytical region
- supporting regions
- filters
- detail/exception region
- approximate x, y, width, and height for major regions and visuals

Avoid a generic equal-card grid unless a target reference requires it.

### 4. Establish hierarchy
Define:
- page identity
- headline information
- dominant analysis
- comparisons/trends
- drivers/breakdowns
- details/exceptions
- controls

Create one clear focal area.

### 5. Choose visual technology
For each major visual select:
- Native Power BI visual
- Deneb
- HTML Content Lite

#### Native visual rule
Use native visuals by default when they meet analytical, design, interaction, accessibility, export, performance, and maintenance needs.

#### Deneb rule
Use Deneb only when it provides a material analytical/design capability not reasonably available natively.

Document:
- native limitation
- analytical benefit
- Vega/Vega-Lite intent
- required fields/measures
- interactions
- accessibility
- performance/row-volume expectations
- export/subscription considerations
- maintenance burden
- fallback

#### HTML Content Lite rule
Use HTML Content Lite only for approved rich presentation components such as narrative/status panels or specialized KPI cards.

Document:
- native limitation
- presentation purpose
- HTML/CSS/data-binding intent
- sanitization/security constraints
- accessibility/fallback
- export/subscription behavior
- performance/maintenance implications

Never include external scripts, remote resources, credentials, unsafe active content, or unsupported HTML.

If approval status is unknown, provide a native fallback and route governance approval through `bi-orchestrator`.

### 6. Apply design references
Map approved design elements to the page.

For target references:
- closely match composition, relative dimensions, hierarchy, styling, navigation, and density
- document deviations

For inspiration references:
- extract patterns without requiring pixel-level replication

### 7. Specify visuals and style
For every visual define:
- purpose and question
- technology and visual type
- measures/dimensions
- region and approximate bounds
- hierarchy
- sorting/ranking
- target/reference/status treatment
- typography/color/surface treatment
- reference/design rule
- analytical states
- accessibility

### 8. Specify interactions
Define cross-filtering, slicers, synchronization, bookmarks, panels, navigation, reset, drill-through, tooltips, back behavior, and disabled interactions.

### 9. Specify analytical states
Define normal, no-data, filtered-empty, blank, zero, not-applicable, missing-target, incomplete-period, stale-data, and error states as applicable.

### 10. Identify dependencies
Route missing measures, fields, KPI definitions, architecture decisions, custom-visual approvals, or unsupported PBIR requirements to owners.

### 11. Obtain design approval
For first pages, material redesigns, target replication, or proposed custom visuals:
- present composition
- present visual technology decisions and fallbacks
- present target-reference mapping and deviations
- wait for approval before PBIR editing

### 12. Prepare PBIR handoff
Provide exact pages, expected files, region geometry, visual inventory, native/Deneb/HTML configuration, approved bindings, formatting, interactions, states, protected areas, and validation requirements to `pbir-report-editing`.

Do not implement PBIR inside this skill.

## Dashboard-ready and push workflow
After PBIR implementation and validation, the agent must report:
`DASHBOARD STATUS: READY FOR PUSH`

Provide exact changed files, validation, limitations, and authorized push commands/handoff.

Do not report push completion until the Git operation succeeds.

After actual success, the authorized agent may report:
`PUSH STATUS: COMPLETE`

Include branch, commit, and remote/PR evidence when available.

## Current screenshot visual QA loop
The user opens/downloads the latest pushed Power BI project and places the screenshots to review under:
`docs/visual-qa/current/`

Rules:
- current screenshots must represent the latest pushed cut
- multiple page images are allowed
- filename should identify the page when practical
- do not use an old screenshot as current evidence
- do not overwrite user screenshots

When QA is requested:
1. inventory readable files in `docs/visual-qa/current/`
2. confirm the associated latest pushed cut
3. map screenshots to pages
4. compare against `design-taste.md`
5. compare target references closely and inspiration references directionally
6. compare approved composition and canvas
7. evaluate visual quality and custom-visual behavior
8. produce evidence-based findings
9. prepare a bounded refinement plan
10. wait for authorized refinement before changing source

After the next push, wait for the user to update `docs/visual-qa/current/` before another QA pass.

## Visual QA criteria

### Composition and hierarchy
- obvious focal point
- dominant and supporting regions
- balanced whitespace and density
- no accidental empty zones or crowding
- primary KPIs/analysis receive suitable prominence

### Reference fidelity
- target designs are replicated closely within stated constraints
- inspiration references are visibly interpreted
- deviations are documented

### Geometry
- margins, alignment, gaps, and repeated sizes are coherent
- no clipping or unintended scrolling

### Visual sophistication
- not a generic equal-card layout
- application-like typography, surfaces, navigation, and rhythm
- brand use remains restrained
- brand colors remain distinct from performance status

### Visual technology
- native visuals used when sufficient
- Deneb is analytically justified and behaves correctly
- HTML Content Lite remains within approved presentation use
- accessibility, export, performance, maintenance, and fallback risks are addressed

### Analytical clarity and accessibility
- visual answers an approved question
- titles and labels are readable
- status directionality is correct
- blank/zero/not-applicable/no-data remain distinct
- contrast and non-color cues are adequate

## Visual QA outcomes
Use exactly one:
- `VISUAL QA: PASS`
- `VISUAL QA: PASS WITH NON-BLOCKING REFINEMENTS`
- `VISUAL QA: REFINEMENT REQUIRED`
- `VISUAL QA: BLOCKED`

Each finding includes:
- QA ID
- severity
- screenshot file/page/region
- observable issue
- affected rule/reference/specification
- proposed refinement
- expected benefit
- owner/artifact

## Controlled refinement
- refine only approved visual/PBIR/theme/custom-visual artifacts
- preserve model/DAX/KPI/source/RLS behavior
- validate and create a new dashboard-ready push handoff
- wait for updated current screenshots after the push
- normally limit to two or three deliberate QA passes unless the user continues

## Boundaries
This skill must not:
- invent/change KPI semantics
- create DAX/model/RLS/source logic
- ignore design-taste
- misclassify target vs inspiration references
- claim unreadable assets were inspected
- assume Deneb/HTML Content Lite approval
- implement PBIR without the editing skill
- claim push or visual QA without evidence

## Completion criteria
- early design advice is bounded and consultative when used
- design sources and filename semantics are explicit
- composition is implementation-ready
- native/Deneb/HTML choices are justified
- target fidelity/deviations are documented
- interactions, states, and accessibility are specified
- dependencies and approvals are assigned
- PBIR handoff requires no invention
- current screenshot QA is evidence-based when performed

## Required output

### Status
Completed | Blocked | Needs decision

### Current mode
Early Design Collaboration | Detailed Design | Visual QA and Refinement

### Early design collaboration
Provide advice, dependencies, feasibility risks, and handoff when applicable.

### Design sources
List policy, target references, inspiration references, theme, and existing precedents.

### Page specification
Provide purpose, audience, questions, KPIs, canvas, composition, regions, visuals, technology choices, styling, interactions, states, and accessibility.

### Custom visual decisions
For Deneb or HTML Content Lite provide justification, approval state, risks, and native fallback.

### Reference fidelity and deviations
Map target/inspiration use and explain deviations.

### Dependencies
List issue, owner, resolution, and blocking status.

### PBIR handoff
Provide all implementation and validation details required by `pbir-report-editing`.

### Dashboard-ready push handoff
Provide status, files, validation, limitations, and authorized Git handoff.

### Visual QA
Provide current screenshot inventory, freshness confirmation, outcome, findings, and refinement plan.
