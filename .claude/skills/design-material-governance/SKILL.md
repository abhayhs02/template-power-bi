---
name: design-material-governance
description: Governs discovery, precedence, interpretation, and safe use of Power BI design references in the repository design-materials folder. Use before every new report page or material visual change, especially when design-taste.md, dashboard-design.pptx, dashboard-design.fig, exported images, themes, icons, or approved PBIR examples may constrain the required look and feel. Never infer content from an unreadable asset.
---
 
# Design Material Governance
 
## Purpose
 
Ensure that report design is controlled by approved repository material instead of generic visual preferences.
 
## Primary consumer
 
- `visual-designer`
 
## Supporting consumers
 
- `pr-reviewer`: verify adherence without implementing fixes.
- `doc-writer`: name accepted design standards and references without redefining them.
 
## Authoritative location
 
Inspect `design-materials/` recursively.
 
The mandatory policy file is:
 
- `design-materials/design-taste.md`
 
Optional approved design references may include:
 
- `design-materials/dashboard-design.pptx`
- `design-materials/dashboard-design.fig`
- exported PNG, JPG, PDF, or SVG references
- approved icons, logos, and image assets
- approved wireframes or page mockups
 
Do not create empty placeholder binary assets.
 
## Precedence
 
Apply design direction in this order:
 
1. Explicit current user instruction
2. `design-materials/design-taste.md`
3. Explicitly approved and readable design reference assets
4. Approved repository theme JSON
5. Existing approved PBIR report style
6. General usability and accessibility conventions
 
A lower-precedence source must not silently override a higher-precedence source.
 
## Workflow
 
### 1. Inventory the directory
 
List every relevant file and record:
 
- path
- format
- size when useful
- readability with available tools
- stated approval/purpose
 
### 2. Read design-taste.md
 
Extract only filled and explicit rules, including:
 
- desired visual character
- grid and spacing
- colors and semantic colors
- typography
- surfaces/cards
- KPI pattern
- charts
- tables/matrices
- filters/navigation
- interactions
- accessibility
- prohibited patterns
 
Unfilled skeleton fields are not design instructions. Mark them unresolved rather than inventing values.
 
### 3. Inspect real reference assets
 
- PPTX: open or render using a supported PowerPoint-reading workflow.
- FIG: inspect only through a supported integration/parser; otherwise request an approved export.
- PNG/JPG/SVG/PDF: inspect through a supported image/document workflow.
 
Never state that an asset was inspected based only on its filename.
 
### 4. Extract observable signals
 
Record only observable or documented signals:
 
- composition
- page proportions
- spacing
- card/container treatment
- typography
- color usage
- navigation
- iconography
- chart/table styling
- filter placement
 
Do not infer animation, hidden interaction, business meaning, or brand approval that is not observable.
 
### 5. Resolve conflicts
 
When sources conflict:
 
- identify the exact conflicting rules
- apply precedence only when the higher source is explicit
- escalate material unresolved conflicts through the orchestrator
- document the approved resolution before implementation
 
## File-handling rules
 
- Do not modify original reference assets unless explicitly asked.
- Do not generate fake PPTX, FIG, or image placeholders.
- Do not commit temporary slide renders or extracted images unless required.
- Do not use sibling-repository assets without authorization.
- Do not expose sensitive brand assets outside approved repository use.
 
## Completion criteria
 
- design-materials was inventoried
- design-taste.md was read
- every used asset was actually inspected
- unreadable or unavailable assets were reported
- binding rules were extracted
- conflicts were resolved or escalated
- downstream design output identifies its sources
 
## Required output
 
### Status
 
Completed | Blocked | Needs decision
 
### Material inventory
 
For each file provide path, format, readable yes/no, approval/purpose, and intended use.
 
### Binding design rules
 
List explicit rules extracted from design-taste.md.
 
### Reference signals
 
List observable patterns extracted from each inspected reference asset.
 
### Conflicts and gaps
 
List conflicting rules, unfilled standards, unreadable assets, and required decisions.
 
### Governed handoff
 
Provide the approved design sources, precedence, binding rules, and limitations to `power-bi-visual-design` or `pr-reviewer`.
