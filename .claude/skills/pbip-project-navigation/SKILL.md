---
name: pbip-project-navigation
description: Locates and explains the repository structure of a Power BI Project, including the .pbip entry file, Report and SemanticModel folders, PBIR definitions, TMDL files, Power Query expressions, DAX measures, theme files, and related documentation. Use before any agent reads or modifies Power BI source so it works against the actual project layout rather than assumed paths.
---
 
# PBIP Project Navigation
 
## Purpose
 
Provide reliable repository discovery for Power BI agents without granting ownership over discovered artifacts.
 
## Shared consumers
 
- `visual-designer`
- `data-modeler`
- `dax-engineer`
- `bi-auditor`
- `pr-reviewer`
- `doc-writer`
- `bi-architect`
 
## Authority rule
 
Discovering a file does not grant permission to modify it. Agent role boundaries remain authoritative.
 
## Workflow
 
### 1. Locate entry points
 
Find:
 
- `.pbip` files
- matching `.Report/` folder
- matching `.SemanticModel/` folder
- multiple projects or thin reports
 
Do not assume one project when multiple exist.
 
### 2. Map report source
 
Identify:
 
- PBIR definition root
- pages/sections
- visual containers
- bookmarks/navigation
- filters/slicers
- tooltip/drill-through pages
- mobile layout
- theme references
- static report resources
 
### 3. Map semantic-model source
 
Identify:
 
- TMDL definition root
- tables/columns/hierarchies
- relationships
- measures/calculation groups
- partitions and Power Query expressions
- roles/RLS
- model metadata
 
### 4. Map supporting repository assets
 
Locate:
 
- `design-materials/`
- `themes/`
- `docs/`
- `tests/`
- `scripts/`
- audit/review reports
- release assets
 
### 5. Return an artifact map
 
Provide project name, entry point, report path, semantic-model path, theme path, design-material path, relevant docs/scripts, and any ambiguity.
 
## Rules
 
- Use actual file discovery, not assumed paths.
- Do not modify files under this skill.
- Do not expose local absolute paths in committed documentation unless required.
- Report missing or ambiguous project structure.
- Do not create fake PBIP/PBIR/TMDL files to satisfy expectations.
 
## Required output
 
### Status
 
Completed | Blocked
 
### Project map
 
List project entry point, report project, semantic-model project, and supporting paths.
 
### Relevant artifact map
 
List files/folders relevant to the caller's task.
 
### Ambiguities
 
List multiple projects, missing components, incompatible formats, or unexpected structure.
 
### Ownership reminder
 
State which agent owns the relevant artifact type.
