# Phase 1 Data Model: Prod‑Kit Overlay README

This is a documentation-only feature. The “data model” here is the document structure and the
concepts it must accurately represent.

## Entities

- **README Section**:
  - `title`: heading text
  - `purpose`: what the section accomplishes
  - `inputs`: prerequisites or required context
  - `steps`: ordered instructions (copy/pasteable)
  - `outputs`: expected repo state after completion

- **Overlay File Set**:
  - `source_repo`: this `prod-kit` repo
  - `target_repo`: an existing Spec‑Kit project
  - `paths`: list of required paths to copy/merge (constitution + templates)
  - `optional_paths`: paths that are agent-specific (e.g., `.claude/commands/*`)

- **Canonical Artifact**:
  - `path`: expected location (e.g., `product/constitution.md`)
  - `purpose`: what it represents
  - `required`: yes/no (minimum viable set vs full set)

## Relationships

- README Section “Overlay” references Overlay File Set.
- README Section “Canonical product artifacts” references Canonical Artifacts.
- README Section “Workflow” references Spec‑Kit phases and maps where Prod‑Kit adds gates.

