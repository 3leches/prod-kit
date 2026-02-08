# Implementation Plan: Prod‑Kit Overlay README

**Branch**: `001-prodkit-layer-readme` | **Date**: 2026-02-08 | **Spec**: `./spec.md`
**Input**: Feature specification from `/specs/001-prodkit-layer-readme/spec.md`

**Note**: This template is filled in by the `/speckit.plan` command. See `.claude/commands/speckit.plan.md` for the execution workflow.

## Summary

Deliver a Spec‑Kit-style `README.md` that explains how to install Specify CLI via `uv tool`,
initialize Spec‑Kit in an existing repo, and then overlay Prod‑Kit (constitution + templates) on
top without forking the Spec‑Kit workflow.

## Technical Context

**Language/Version**: Markdown (GitHub-flavored Markdown)  
**Primary Dependencies**: None (documentation only)  
**Storage**: N/A  
**Testing**: Manual validation (README walkthrough + link/path checks)  
**Target Platform**: GitHub repository (public docs)  
**Project Type**: Documentation-only change  
**Performance Goals**: N/A  
**Constraints**: MUST preserve overlay approach (augment Spec‑Kit, don’t fork workflow); commands and
paths MUST be copy/pasteable; keep steps minimal and consistent with `.specify/memory/constitution.md`  
**Scale/Scope**: One README + supporting spec artifacts for this feature

## Constitution Check

*GATE: Must pass before Phase 0 research. Re-check after Phase 1 design.*

Gates derived from `/.specify/memory/constitution.md` (Prod‑Kit Constitution):

- [ ] **Product Constitution exists**: This repo is a framework/overlay repo, not a product repo with
      `product/constitution.*`. We treat `.specify/memory/constitution.md` as the governing durable
      artifact for Prod‑Kit itself. (Justified in Complexity Tracking.)
- [x] **Purpose is explicit**: Captured in `spec.md` Product Context and user stories.
- [x] **Scope is bounded**: This feature is limited to README onboarding + overlay instructions.
- [ ] **Traceability**: The spec references KPI categories conceptually, but does not link to concrete
      `kpis/*` and `workflows/*` files because those live in the *user’s* product repo, not here.
      (Justified in Complexity Tracking.)
- [x] **Augmentation, not replacement**: README explicitly describes Prod‑Kit as an overlay.
- [x] **Instrumentation decision recorded**: Documentation-only; no product KPI instrumentation is
      applicable to implement in this repo.

## Project Structure

### Documentation (this feature)

```text
specs/001-prodkit-layer-readme/
├── plan.md              # This file (/speckit.plan command output)
├── research.md          # Phase 0 output (/speckit.plan command)
├── data-model.md        # Phase 1 output (/speckit.plan command)
├── quickstart.md        # Phase 1 output (/speckit.plan command)
├── contracts/           # Phase 1 output (/speckit.plan command)
└── tasks.md             # Phase 2 output (/speckit.tasks command - NOT created by /speckit.plan)
```

### Source Code (repository root)

```text
README.md
.specify/
├── memory/
│   └── constitution.md
└── templates/
    ├── plan-template.md
    ├── spec-template.md
    └── tasks-template.md

specs/001-prodkit-layer-readme/
├── spec.md
├── plan.md
└── checklists/
    └── requirements.md
```

**Structure Decision**: Documentation-only change within this repo, primarily `README.md`, with spec
and checklist artifacts under `specs/001-prodkit-layer-readme/`.

## Complexity Tracking

> **Fill ONLY if Constitution Check has violations that must be justified**

| Violation | Why Needed | Simpler Alternative Rejected Because |
|-----------|------------|-------------------------------------|
| No `product/constitution.*` in this repo | This is a framework/overlay repo; the durable governance artifact is `.specify/memory/constitution.md`, not a single product constitution | Adding `product/constitution.md` here would imply Prod‑Kit itself is a product with ICP/value/metrics, which is misleading for an overlay toolkit |
| No concrete `kpis/*` or `workflows/*` links for this feature | The README instructs users to create these in *their* product repo; this repo documents canonical locations and gates | Creating example `kpis/` and `workflows/` content in this repo would shift scope from “how to overlay” to “ship a sample product” |
