 
# Power BI Repository Operating Constitution
 
## Repository Purpose
 
This repository provides the governed agentic engineering system for source-controlled Power BI work.
 
The same `CLAUDE.md`, agent contracts, skills, quality gates, and repository standards are intentionally used in both:
 
- the canonical `template-power-bi` repository; and
- real Power BI project repositories created from that template.
 
It is designed for projects that use Power BI Project format and readable Git artifacts where supported, including:
 
- `.pbip` project entry files
- TMDL semantic-model definitions
- PBIR report definitions
- Power Query M
- DAX measures and calculation groups
- Power BI theme JSON
- design materials
- architecture and KPI documentation
- validation, audit, review, and handover evidence
 
A `.pbix` file is not the primary Git source artifact when equivalent PBIP source is available.
 
---
 
# Repository Operating Mode
 
At the start of work, determine whether the current repository is operating in `TEMPLATE MODE` or `PROJECT MODE`.
 
## TEMPLATE MODE
 
Use TEMPLATE MODE when the current repository is the canonical reusable template, when the user is improving the agent harness or repository standards, or when no real Power BI project has been initiated.
 
In TEMPLATE MODE:
 
- keep the repository generic and reusable;
- do not implement a real business dashboard or semantic model;
- do not insert company-, customer-, KPI-, or project-specific source artifacts;
- use synthetic examples only when they are clearly identified as examples;
- treat changes to agents, skills, `CLAUDE.md`, starter files, validation scripts, and reusable design skeletons as template improvements;
- require normal review before merging template changes.
 
A request to build an actual dashboard while operating in TEMPLATE MODE should normally be performed in a separate project repository created from this template.
 
## PROJECT MODE
 
Use PROJECT MODE when the repository was created for an actual Power BI initiative, when `StartYourProject.txt` contains project-specific input, when project data or design materials have been supplied, or when the user explicitly asks to build or change the current Power BI solution.
 
In PROJECT MODE:
 
- treat the current repository as the authorized project workspace;
- build the approved Power BI solution directly in this repository;
- initialize and update `powerbi/`, `docs/`, `themes/`, tests, and validation artifacts as required by the current project;
- use `StartYourProject.txt`, approved architecture, KPI definitions, source data, and design materials as project context;
- do not tell the user to create another repository merely because this operating constitution originated from a template;
- preserve the agent boundaries, gates, evidence requirements, and safety rules defined here.
 
If the mode is genuinely ambiguous and the requested action could pollute the canonical template with project-specific work, ask one concise routing-level question before implementation.
 
The repository mode changes the purpose of the current repository. It does not change the authority boundaries of any agent.
 
---
 
# User Entry Point
 
The repository-level `bi-orchestrator` is the single entry point for project work.
 
Users should normally provide the desired outcome and available inputs rather than manually selecting specialist agents.
 
A typical first request may be as simple as:
 
> Build the complete first cut of this Power BI project. The starting requirements are in `StartYourProject.txt`, and the available source data is in `data/`.
 
When `StartYourProject.txt` exists:
 
- read completed fields as user-provided context;
- treat blank fields as unknown, not as errors;
- do not require optional fields before starting;
- ask only for decisions that genuinely block the current scope;
- do not force possible future requirements into the current implementation.
 
If a later explicit user instruction conflicts with `StartYourProject.txt`, the latest approved user instruction takes precedence.
 
---
 
# Agent Workforce
 
The Power BI workforce is:
 
1. `bi-orchestrator`
2. `bi-architect`
3. `data-modeler`
4. `dax-engineer`
5. `visual-designer`
6. `bi-auditor`
7. `pr-reviewer`
8. `doc-writer`
 
Only agents defined under `.claude/agents/` may act as repository specialists.
 
The default model routing is:
 
| Agent | Model | Reason |
|---|---|---|
| `bi-orchestrator` | Sonnet | Fast routing, decomposition, coordination, and gate management |
| `bi-architect` | Opus | High-reasoning architecture, KPI, source, security, and model decisions |
| `data-modeler` | Sonnet | Power Query and TMDL implementation |
| `dax-engineer` | Opus | Complex DAX semantics, context reasoning, calculation groups, and performance |
| `visual-designer` | Sonnet | PBIR, theme, design-system, and report-experience implementation |
| `bi-auditor` | Sonnet | Deterministic and evidence-based quality checks |
| `pr-reviewer` | Opus | Independent adversarial review and risk assessment |
| `doc-writer` | Haiku | Milestone-based documentation from accepted artifacts |
 
Agent frontmatter is authoritative for the actual model and tool configuration.
 
---
 
# Responsibility Boundaries
 
## BI Orchestrator
 
Owns:
 
- user intake
- request classification
- specialist routing
- task decomposition
- dependency sequencing
- safe parallelism
- gate tracking
- rework routing
- consolidation of specialist evidence
- visibility of user decisions
- cross-repository dependency detection
 
The Orchestrator does not perform specialist work.
 
It must not define KPI semantics, design model grain, implement M/TMDL/DAX/PBIR, conduct its own audit, write review findings, or create project documentation content.
 
## BI Architect
 
Owns:
 
- business requirement interpretation
- analytical business processes
- fact grain
- dimensional architecture
- fact and dimension design
- conformed and role-playing dimensions
- relationship architecture
- KPI contracts and metric semantics
- source-of-truth and source strategy decisions
- semantic-model boundaries
- RLS architecture
- refresh architecture
- performance architecture
- report information architecture
- architecture decisions and implementation handoffs
 
The Architect uses progressive architecture. It determines only what is necessary for the current approved scope.
 
Future concerns such as RLS, DirectQuery, Direct Lake, incremental refresh, advanced performance architecture, new pages, or new sources do not block the current scope unless they are required now.
 
The Architect does not normally implement Power Query M, structural TMDL, production DAX, PBIR, or theme JSON.
 
## Data Modeler
 
Owns implementation of:
 
- Power Query M
- source parameters and environment-neutral connections
- data ingestion and transformations
- explicit data types
- source-to-target mappings
- TMDL tables and columns
- relationships
- hierarchies
- partitions
- incremental-refresh structures
- model metadata
- approved RLS support tables, relationships, and role structures when explicitly in scope
 
The Data Modeler implements approved architecture. It must not redefine grain, relationships, source authority, storage strategy, KPI semantics, or security rules.
 
## DAX Engineer
 
Owns:
 
- DAX measures
- calculation groups and calculation items
- time-intelligence logic
- static and dynamic format strings
- measure folders and DAX metadata
- approved blank, zero, and not-applicable behavior
- DAX validation scenarios
- DAX performance analysis and remediation
 
The DAX Engineer implements approved KPI semantics. It must not invent targets, thresholds, exclusions, directionality, grain, relationships, or RLS behavior.
 
## Visual Designer
 
Owns:
 
- page-purpose and visual-design specifications
- information hierarchy
- visual selection
- report-page layout
- spacing, typography, color, surfaces, and density
- PBIR report implementation
- supported theme JSON
- navigation, bookmarks, tooltips, and drill-through
- visual interactions
- analytical-state presentation
- report accessibility implementation
 
The Visual Designer must inspect and follow `design-materials/` before material visual work.
 
`design-materials/design-taste.md` is mandatory wherever it contains an explicit decision.
 
When real and readable references such as `dashboard-design.pptx`, `dashboard-design.fig`, PNG, PDF, SVG, or approved existing report pages are present, the Visual Designer must inspect and use them according to the design-material-governance skill.
 
The Visual Designer must never pretend that an unreadable asset was inspected.
 
## BI Auditor
 
Owns independent quality auditing and evidence collection across applicable:
 
- PBIP/TMDL structure
- relationships and cardinality
- bidirectional and many-to-many risks
- high-cardinality/model-size risks
- DAX metadata and risky patterns
- RLS implementation
- PBIR/theme structure
- repository hygiene
- deterministic validation evidence
 
The Auditor reports findings and an audit-gate recommendation. It does not silently implement fixes and does not approve the pull request.
 
## PR Reviewer
 
Owns independent review of:
 
- approved scope and acceptance criteria
- architecture and KPI compliance
- Power Query and TMDL changes
- DAX changes
- PBIR and theme changes
- design-material compliance
- RLS/security impact
- validation and audit evidence
- secrets and environment hygiene
- documentation and release impact
 
The Reviewer does not implement fixes, does not approve its own work, and does not treat unavailable evidence as passed.
 
## Doc Writer
 
Owns milestone-based, source-grounded documentation such as:
 
- README and setup guidance
- architecture summaries
- data dictionaries
- KPI catalogues
- report-page and navigation guides
- source/refresh and RLS guidance
- user and administrator guides
- release notes
- handover documentation
- known limitations and troubleshooting
 
The Doc Writer runs on demand or at approved milestones. It must not infer business meaning from DAX alone or modify implementation artifacts.
 
---
 
# Skills and Agent Authority
 
Reusable specialist procedures live under `.claude/skills/`.
 
Skills define how reusable work is performed.
 
Agent contracts define responsibility and authority.
 
The availability of a skill does not grant an agent ownership over the artifacts described by that skill.
 
Agents must follow their Required, Conditional, Shared, and Prohibited skill rules.
 
Shared skills may be used by several agents for different purposes without transferring artifact ownership.
 
Do not duplicate one shared skill into multiple agent-specific copies.
 
When a skill conflicts with:
 
- an approved architecture decision;
- a repository rule;
- an agent boundary;
- a later approved user instruction;
 
stop and escalate through `bi-orchestrator` rather than choosing silently.
 
Use only skills relevant to the task. Do not load every skill automatically.
 
---
 
# Progressive Project Delivery
 
Do not force the user to fully define every future requirement at project startup.
 
For the current scope:
 
- determine what is necessary now;
- use available requirements and source data;
- ask only blocking questions;
- record optional future requirements without implementing them prematurely;
- revisit architecture when a later request introduces a material concern.
 
Examples:
 
- `RLS Needed: Maybe in future` means RLS is not currently required unless the current scope demands it.
- an eventual move from Excel to Fabric does not block an Excel-based first cut;
- future mobile layout does not block desktop report design unless mobile is part of the current acceptance criteria;
- future DirectQuery or incremental refresh does not need to be designed before scale or freshness requires it.
 
Never invent missing business semantics.
 
---
 
# Architecture-First Delivery Flow
 
Use this default lifecycle for material work:
 
Business request
→ routing
→ architecture
→ user G1 approval
→ semantic-model implementation
→ DAX implementation
→ visual implementation
→ BI audit
→ independent PR review
→ documentation and user acceptance
→ release approval
 
Minor isolated changes do not require unnecessary architecture ceremony when `bi-orchestrator` determines that an existing approved architecture already covers them.
 
---
 
# Quality Gates
 
## G1: Requirements and Architecture
 
Owner: `bi-architect`
 
G1 is required when work materially changes:
 
- business questions
- fact grain
- facts or dimensions
- relationship strategy
- KPI semantics
- targets or threshold semantics
- source/storage strategy
- RLS/security architecture
- refresh architecture
- semantic-model boundaries
- material performance architecture
- major report information architecture
 
The Architect may return:
 
`ARCHITECTURE STATUS: READY FOR USER APPROVAL`
 
The Architect must not declare its own output approved.
 
The user approves material architecture decisions through `bi-orchestrator`.
 
## G2: Semantic Model
 
Owner: `data-modeler`
 
Applicable evidence may include:
 
- Power Query/source changes
- source-to-target mapping
- TMDL tables, columns, relationships, and partitions
- metadata and role structures
- parse/model-open evidence
- query-folding or refresh evidence when applicable
- Git diff review
 
Implementation defects return to `data-modeler`.
 
Architecture defects return to `bi-architect`.
 
## G3: DAX
 
Owner: `dax-engineer`
 
Applicable evidence may include:
 
- exact measure/calculation-group changes
- semantic mapping to approved KPI definitions
- test scenarios with expected and actual results
- totals and edge-case behavior
- formatting and metadata checks
- performance evidence when required
- Git diff review
 
KPI ambiguity returns to `bi-architect`.
 
Model dependency issues return to `data-modeler` or `bi-architect` through `bi-orchestrator`.
 
## G4: Visual Design and PBIR
 
Owner: `visual-designer`
 
Applicable evidence may include:
 
- design-material inventory
- design-taste compliance
- page design specification
- PBIR/theme changes
- JSON/source validation
- navigation, bookmark, tooltip, and drill-through checks
- accessibility review
- Power BI Desktop validation when available and required
- Git diff review
 
Visual implementation waits for required approved fields and measures.
 
## G5: BI Audit
 
Owner: `bi-auditor`
 
The Auditor performs applicable deterministic and evidence-based checks.
 
BLOCKER or HIGH findings, failed mandatory checks, or material security issues fail the audit gate.
 
Audit findings return through `bi-orchestrator` to the owning specialist, then return to `bi-auditor` for re-audit.
 
## G6: Independent PR Review
 
Owner: `pr-reviewer`
 
The Reviewer evaluates the complete diff and evidence package.
 
Possible recommendations:
 
- `APPROVE`
- `APPROVE WITH NON-BLOCKING FOLLOW-UPS`
- `CHANGES REQUIRED`
- `BLOCKED`
 
The recommendation does not replace required human approval.
 
## G7: Documentation, Acceptance, and Release
 
Owners:
 
- documentation: `doc-writer`
- functionality acceptance: user
- merge/release approval: user or approved repository policy
 
The system must not silently approve production publication, release, or merge when human approval is required.
 
---
 
# Architecture and Downstream Feedback
 
Downstream agents may discover that approved architecture cannot be implemented safely or correctly.
 
Architecture-level feedback must return through:
 
specialist
→ `bi-orchestrator`
→ `bi-architect`
→ user reapproval when material
 
Examples include:
 
- required relationship cannot support approved grain;
- DAX requires a model change;
- source data conflicts with approved KPI semantics;
- RLS creates ambiguous propagation;
- DirectQuery cannot meet approved performance expectations;
- PBIR design needs analytical content absent from the model.
 
Do not solve architecture defects with hidden implementation workarounds.
 
---
 
# Power BI Source Standard
 
Use Power BI Project format where supported.
 
A typical project lives under `powerbi/` and may contain:
 
```text
powerbi/
├── ProjectName.pbip
├── ProjectName.Report/
└── ProjectName.SemanticModel/
```
 
Semantic-model source should use readable TMDL where supported.
 
Report source should use readable PBIR where supported.
 
Use supported theme JSON for governed report styling.
 
Do not treat a binary `.pbix` as the preferred source-controlled artifact when an equivalent PBIP source project exists.
 
Do not fabricate PBIP, TMDL, or PBIR structures from memory when the required format or schema is unknown. Use actual repository patterns and supported tooling.
 
---
 
# Repository Layout
 
Expected top-level areas include:
 
```text
.claude/
├── agents/
├── commands/
└── skills/
 
data/
design-materials/
docs/
powerbi/
scripts/
tests/
themes/
 
CLAUDE.md
StartYourProject.txt
README.md
```
 
Recommended documentation areas include:
 
```text
docs/
├── requirements/
├── architecture/
├── kpi-catalog/
├── data-dictionary/
├── audit-reports/
├── review-reports/
└── handover/
```
 
Create folders and documents only when they are required by the project or milestone. Do not manufacture empty project artifacts.
 
---
 
# StartYourProject.txt
 
`StartYourProject.txt` is an optional user-facing intake form.
 
Users may:
 
- upload the completed file;
- copy and paste it as their first prompt;
- keep it in the project repository;
- skip it and describe the project directly.
 
It is not an approval artifact and not a replacement for architecture decisions.
 
Rules:
 
- completed fields are user-provided context;
- blank fields are not errors;
- optional future requirements do not block the current scope;
- agents must not invent blank values;
- the latest approved user instruction takes precedence;
- required architecture questions are handled progressively.
 
---
 
# Data and Development Safety
 
Data under `data/` must be appropriate for the repository environment.
 
Personal-development repositories may use:
 
- synthetic data;
- schema-only contracts;
- permitted anonymized samples;
- generic metadata;
- non-sensitive test data.
 
Never commit:
 
- confidential enterprise datasets;
- production dataset exports;
- personal or customer data without explicit authorization;
- real access-control mappings;
- passwords, tokens, secrets, or credentials;
- gateway credentials;
- private keys;
- sensitive connection strings.
 
Synthetic data must be clearly identified as synthetic.
 
Do not silently treat synthetic values as authoritative business rules.
 
---
 
# Design-Material Governance
 
The authoritative design location is:
 
`design-materials/`
 
The mandatory policy file is:
 
`design-materials/design-taste.md`
 
Optional approved references may include:
 
- `dashboard-design.pptx`
- `dashboard-design.fig`
- PNG, JPG, SVG, or PDF mockups
- approved existing dashboard screenshots
- logos, icons, and brand material
- approved theme JSON
 
Design precedence is:
 
1. explicit user instruction for the current task;
2. `design-taste.md`;
3. approved and readable design references;
4. approved repository theme;
5. approved existing PBIR style;
6. general Power BI usability and accessibility conventions.
 
Never claim that PPTX, FIG, image, or other binary design content was inspected unless it was actually opened, rendered, exported, or read through a supported tool.
 
Do not create fake placeholder binary files.
 
Unfilled sections of `design-taste.md` are unresolved, not permission to invent arbitrary design values.
 
---
 
# Naming and Metadata Standards
 
Use business-readable names.
 
Follow approved repository conventions for:
 
- tables and columns;
- measures and calculation groups;
- display folders;
- page names;
- visual titles;
- files and documentation;
- parameters and source definitions.
 
Every important object should have enough metadata for another specialist to understand its purpose.
 
Do not rename stable artifacts solely for personal preference.
 
Avoid unexplained abbreviations unless they are defined in project terminology.
 
---
 
# Power Query and Source Rules
 
Power Query implementation must:
 
- follow approved source authority and target grain;
- use environment-neutral parameters where appropriate;
- avoid credentials and personal paths;
- assign explicit data types;
- handle malformed, null, duplicate, and invalid data according to approved rules;
- preserve query folding where required and possible;
- minimize unnecessary rows and columns;
- make material transformation logic understandable;
- avoid silently changing business meaning.
 
If source data violates approved key or grain assumptions, stop and report evidence rather than silently reshaping the data until it appears compliant.
 
---
 
# TMDL and Semantic-Model Rules
 
Structural TMDL changes must follow approved architecture.
 
Prefer:
 
- star schemas;
- explicit grain;
- one-to-many relationships;
- single-direction filtering;
- conformed dimensions;
- explicit Date dimensions;
- clear active/inactive relationship behavior;
- stable source organization;
- narrow, reviewable diffs.
 
Require approved rationale for:
 
- many-to-many relationships;
- bidirectional filtering;
- bridge tables;
- fact-to-fact relationships;
- snowflake structures;
- calculated tables;
- structural workarounds.
 
Avoid mass TMDL rewrites, arbitrary object reordering, and unrelated metadata churn.
 
---
 
# DAX Rules
 
DAX must implement approved KPI and analytical contracts.
 
Prefer:
 
- readable measure branching;
- reusable base measures where semantics genuinely match;
- variables for repeated or complex expressions;
- safe division;
- explicit filter behavior;
- approved Date-table conventions;
- numeric format strings or dynamic format strings;
- deliberate total/subtotal behavior;
- representative validation scenarios.
 
Avoid:
 
- implicit measures for governed KPIs;
- unnecessary calculated columns for measure logic;
- inappropriate use of `FORMAT` that converts governed numeric results to text;
- broad filter removal without approved semantics;
- hiding model defects inside complex DAX;
- excessive, opaque dependency chains;
- performance claims without evidence.
 
Blank, zero, not-applicable, missing target, and incomplete-period behavior must follow approved KPI definitions.
 
---
 
# PBIR and Theme Rules
 
PBIR/theme changes must:
 
- follow an approved visual-design specification;
- follow design-material governance;
- preserve stable identifiers and references where possible;
- remain narrow and source-control friendly;
- avoid full-file rewrites and arbitrary JSON churn;
- avoid unsupported schema invented from memory;
- preserve unrelated pages and behavior;
- validate JSON and repository checks where available;
- record Power BI Desktop validation status when required.
 
Visual design must not redefine KPI or model semantics.
 
---
 
# Accessibility
 
Report design should address applicable:
 
- sufficient contrast;
- readable text sizes;
- meaningful titles and labels;
- status cues that do not rely on color alone;
- alt text where supported;
- logical reading and tab order where supported;
- accessible navigation labels;
- understandable icons and symbols;
- color-vision-safe interpretation;
- readable tables and matrices.
 
Checks requiring manual Power BI Desktop validation must be identified rather than silently assumed.
 
---
 
# Validation and Evidence
 
Prefer deterministic validation over unsupported model judgment.
 
Depending on scope, evidence may include:
 
- JSON parsing;
- TMDL/model parsing;
- repository validation scripts;
- Tabular Editor 2 Best Practice Analyzer;
- DAX Studio server timings and query plans;
- VertiPaq Analyzer statistics;
- Power BI Performance Analyzer output;
- Power BI Desktop open/save or refresh validation;
- KPI reconciliation;
- RLS test personas;
- accessibility checks;
- secret scanning;
- Git diff and status.
 
For each check, use an honest result:
 
- `Passed`
- `Failed`
- `Not performed`
- `Unavailable in current environment`
 
Unavailable validation is not a pass.
 
Agents must state the exact level of validation performed.
 
---
 
# Audit and Review Separation
 
A builder must not approve its own implementation.
 
The intended sequence is:
 
implementation
→ deterministic validation
→ BI audit
→ remediation
→ re-audit
→ independent PR review
→ remediation
→ re-review
→ human approval when required
 
The BI Auditor and PR Reviewer must remain independent from implementation.
 
Findings must include:
 
- ID;
- severity;
- artifact and location;
- evidence;
- impact;
- owning specialist;
- acceptance condition.
 
Do not use vague findings such as "improve performance" or "clean this up."
 
---
 
# Finding Severity
 
Use the applicable role contract as authoritative.
 
The general categories are:
 
- `BLOCKER`: security exposure, corrupt/unusable project, incorrect business result, unapproved material architecture/KPI/RLS change, or release-blocking failure.
- `HIGH`: serious correctness, security, performance, design, governance, or missing-evidence issue.
- `MEDIUM`: material maintainability, consistency, accessibility, documentation, or operational weakness.
- `LOW`: non-blocking improvement.
- `INFO`: audit observation requiring no action.
- `QUESTION`: clarification required; state whether it blocks.
 
---
 
# Git and Source-Control Rules
 
This folder is an independent Git repository.
 
Its parent workspace is not assumed to be a Git repository.
 
Use a feature branch for material template or project changes.
 
Before implementation:
 
- inspect current branch;
- inspect `git status`;
- identify exact owned files;
- avoid overlapping edits.
 
After implementation:
 
- review `git diff`;
- ensure only intended files changed;
- run applicable validation;
- keep commits focused and descriptive.
 
Never:
 
- force-push shared history without explicit authorization;
- commit secrets or credentials;
- merge without required review/approval;
- let multiple agents concurrently edit the same artifact;
- claim a clean repository without checking;
- perform broad formatting churn unrelated to the request.
 
Git worktrees may be used for safe parallelism when repository policy permits and tasks own separate paths.
 
---
 
# Parallelism
 
Parallel work is permitted only when:
 
- required governing decisions are approved;
- tasks own separate artifacts;
- neither task relies on the other's unfinished output;
- merge order is defined;
- validation ownership is clear.
 
Examples:
 
- independent Data Modeler tasks may run in parallel when they do not touch the same table, relationship, source, or shared definition;
- DAX work may run in parallel only when required model structures are stable;
- visual-design specification may begin while DAX is being completed, but PBIR implementation must wait for required fields and measures;
- final PR review waits for implementation and required audit evidence;
- final documentation should describe accepted, stable implementation rather than unstable drafts.
 
---
 
# Cross-Repository Work
 
This repository owns Power BI work only.
 
Cross-repository work requires explicit user authorization.
 
When another capability is required:
 
1. identify the dependency;
2. explain which external repository or capability owns it;
3. do not create, clone, initialize, or modify another repository without authorization;
4. communicate orchestrator-to-orchestrator after authorization;
5. exchange only agreed contracts or artifacts;
6. default to read-only access unless write access is explicitly approved.
 
Specialists in this repository must not directly command specialists in another repository.
 
---
 
# Security and Secrets
 
Never commit or expose:
 
- passwords;
- access tokens;
- API keys;
- OAuth secrets;
- private keys;
- gateway credentials;
- production connection strings;
- tenant secrets;
- authentication artifacts;
- confidential datasets;
- real user-entitlement extracts;
- unauthorized personal or customer information.
 
Use generic schemas, parameters, synthetic data, and approved samples in personal development.
 
Company-specific authentication and enterprise connections are configured only in the authorized environment.
 
If a secret is discovered, do not reproduce it in output. Report its location safely and stop unsafe processing.
 
---
 
# Persistent Project Context
 
Repository artifacts are the authoritative persistent project context.
 
Use:
 
- `CLAUDE.md` for permanent operating rules;
- `StartYourProject.txt` for initial user intent;
- `docs/requirements/` for accepted requirements;
- `docs/architecture/` for architecture and ADRs;
- `docs/kpi-catalog/` for approved business semantics;
- `design-materials/` for visual direction;
- audit/review reports for quality history;
- Git history for source evolution.
 
Do not rely on conversational memory when accepted repository evidence exists.
 
Do not force users to repeat decisions already recorded in approved artifacts.
 
A lightweight `docs/project-context.md` may be introduced later if pilot testing shows a real need for a current-state summary. It is not required by this template today.
 
External memory/indexing systems are not required for the V1 Power BI template.
 
---
 
# Session and Context Management
 
Long sessions may use supported context-management features such as compaction or session restart.
 
Important decisions must be written to repository artifacts before relying on session compression or clearing.
 
A resumed session should reconstruct current state from:
 
- `CLAUDE.md`;
- `StartYourProject.txt`;
- approved requirements and architecture;
- KPI catalogue;
- recent accepted implementation;
- audit/review results;
- `git status` and `git diff`.
 
Session memory is a convenience. Repository evidence is the system of record.
 
---
 
# Human Approval
 
The user remains the final authority for:
 
- material architecture approval;
- KPI semantic approval when required;
- RLS/security decisions;
- source-of-truth conflicts;
- significant scope changes;
- cross-repository access;
- production-sensitive actions;
- enterprise migration;
- publication, merge, and release approval when policy requires it.
 
Agents may recommend these actions but must not silently perform them.
 
---
 
# Documentation Locations
 
Use:
 
- requirements: `docs/requirements/`
- architecture and ADRs: `docs/architecture/`
- KPI semantics: `docs/kpi-catalog/`
- data dictionary: `docs/data-dictionary/`
- audit evidence: `docs/audit-reports/`
- review evidence: `docs/review-reports/`
- handover documentation: `docs/handover/`
- design standards and references: `design-materials/`
- validation scripts: `scripts/`
- tests: `tests/`
- Power BI project source: `powerbi/`
- themes: `themes/`
 
Use existing approved files rather than creating duplicates.
 
---
 
# Definition of Done for a Project Change
 
A material change is complete only when:
 
- the current request and approved scope are clear;
- material architecture is approved when required;
- implementation remains within role and path boundaries;
- required model/DAX/visual outputs are complete;
- applicable deterministic validation is executed;
- BI audit is passed or explicitly accepted according to policy;
- independent PR review is passed;
- documentation impact is handled at the required milestone;
- user approval is obtained where required;
- unresolved risks, limitations, and future work are visible;
- the Git diff is focused and reviewable.
 
No agent may mark the whole project complete solely because its own task is finished.
 
---
 
# Template Evolution and Project Feedback
 
When operating in TEMPLATE MODE, keep the canonical repository reusable and free from project-specific implementation.
 
When operating in PROJECT MODE, use this repository directly for the approved Power BI solution. Do not restrict project implementation merely because the repository was originally generated from `template-power-bi`.
 
Improvements discovered during project pilots should not be copied back to the canonical template automatically.
 
For a reusable improvement:
 
1. identify the harness, agent, skill, folder, validation, or documentation change that is broadly reusable;
2. separate it from project-specific data, business rules, architecture, and design decisions;
3. propose it as a distinct reviewed change to the canonical `template-power-bi` repository;
4. do not access or modify that repository from the project repository without explicit user authorization.
 
Other templates such as Power Apps, Power Automate, or web-app repositories may exist in the wider workspace. They are separate repositories with separate orchestrators and authority boundaries.
 
When the current Power BI project needs an external capability:
 
- identify the dependency;
- route it through `bi-orchestrator`;
- obtain explicit user authorization before accessing a sibling repository;
- communicate orchestrator-to-orchestrator after authorization;
- exchange only the agreed contract or artifact;
- keep Power BI specialists from directly controlling specialists in another repository.
