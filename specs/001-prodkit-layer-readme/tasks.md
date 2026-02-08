---

description: "Task list for README onboarding + upgrade paths"
---

# Tasks: Prod‑Kit Overlay README

**Input**: Design documents from `/specs/001-prodkit-layer-readme/`
**Prerequisites**: `plan.md` (required), `spec.md` (required), `research.md`, `data-model.md`,
`contracts/`, `quickstart.md`

**Tests**: Not requested for this documentation-only feature.

**Organization**: Tasks are grouped by user story to enable independent delivery and validation.

## Format: `[ID] [P?] [Story] Description`

- **[P]**: Can run in parallel (different files, no dependencies)
- **[Story]**: Which user story this task belongs to (e.g., US1, US2, US3)
- Include exact file paths in descriptions

## Phase 1: Setup (Shared Infrastructure)

**Purpose**: Ensure docs inputs and structure are ready

- [x] T001 Confirm feature artifacts exist in `specs/001-prodkit-layer-readme/` (spec.md, plan.md, research.md, data-model.md, quickstart.md, contracts/)
- [x] T002 [P] Validate all README-referenced paths exist in this repo (`.specify/memory/constitution.md`, `.specify/templates/*`, `.claude/commands/*`)
- [x] T003 [P] Validate Spec‑Kit upstream reference is correct in `README.md` (Spec‑Kit link + repo name)

---

## Phase 2: Foundational (Blocking Prerequisites)

**Purpose**: Shared requirements that MUST be true before refining any user-story sectioning

**⚠️ CRITICAL**: No user story work can begin until this phase is complete

- [x] T004 Define the “overlay file set” (required vs optional) and keep it consistent across `README.md` and `specs/001-prodkit-layer-readme/quickstart.md`
- [x] T005 Normalize terminology in `README.md` (Spec‑Kit, Specify CLI, Prod‑Kit overlay, constitution/templates, gates)
- [x] T006 Ensure README statements align with `.specify/memory/constitution.md` (augmentation-not-replacement + canonical artifact structure)

**Checkpoint**: Foundation ready — user story sections can now be refined

---

## Phase 3: User Story 1 - Layer Prod‑Kit onto an existing Spec‑Kit project (Priority: P1) 🎯 MVP

**Goal**: A user can install Specify CLI, initialize Spec‑Kit, then overlay Prod‑Kit templates and
constitution without changing the Spec‑Kit workflow.

**Independent Test**: Follow `README.md` from a clean Spec‑Kit repo and confirm:
- The overlay copy list is explicit (required vs optional)
- The user ends with the documented file structure and can proceed with `/speckit.*` commands

### Implementation for User Story 1

- [x] T007 [US1] Add/verify Spec‑Kit install + init steps in `README.md` (include `uv tool install ...` and `uvx ...` options)
- [x] T008 [US1] Add/verify explicit overlay copy/merge steps in `README.md` (list required overlay files and optional `.claude/commands/*`)
- [x] T009 [US1] Ensure `README.md` includes a minimal quickstart command sequence for the normal flow (`/speckit.constitution` → `/speckit.specify` → `/speckit.plan` → `/speckit.tasks` → `/speckit.implement`)
- [x] T010 [US1] Keep `specs/001-prodkit-layer-readme/quickstart.md` consistent with `README.md` overlay instructions (same commands + same overlay file set)

**Checkpoint**: A user can complete overlay setup using only the README

---

## Phase 4: User Story 2 - Understand what Prod‑Kit changes (Priority: P2)

**Goal**: A user can understand what Prod‑Kit adds vs what stays unchanged, and the canonical artifact
structure to add to their own repo.

**Independent Test**: A reader can answer:
- “What does Prod‑Kit add?”
- “Which Spec‑Kit phases remain the same?”
- “Which artifacts do I add and where do they live?”

### Implementation for User Story 2

- [x] T011 [US2] Ensure positioning is clear in `README.md` (“Spec‑Kit: what” vs “Prod‑Kit: why/for whom/how measured”) and states “overlay/augment” (not fork)
- [x] T012 [US2] Document canonical product artifact structure in `README.md` and ensure it matches `.specify/memory/constitution.md`
- [x] T013 [US2] Document workflow mapping in `README.md` (clarify/specify/plan/tasks) and explain where Prod‑Kit adds gates/templates
- [x] T014 [US2] Ensure the Governance section in `README.md` points to `.specify/memory/constitution.md` as canonical

**Checkpoint**: A user can explain Prod‑Kit’s scope and required artifacts without confusion

---

## Phase 5: User Story 3 - Upgrade and maintenance guidance (Priority: P3)

**Goal**: A maintainer can upgrade upstream Spec‑Kit/Specify CLI and independently upgrade the
Prod‑Kit overlay, without losing Prod‑Kit gates.

**Independent Test**: A maintainer can follow the README and:
- Upgrade Specify CLI
- Upgrade Spec‑Kit templates/commands (upstream) and then re-apply Prod‑Kit overlay
- Validate that the three overlay template changes still exist

### Implementation for User Story 3

- [x] T015 [US3] Add/verify “Upgrading Spec‑Kit / Specify CLI” steps in `README.md` (include `uv tool install ... --force` upgrade command)
- [x] T016 [US3] Add/verify “Upgrading Prod‑Kit overlay” steps in `README.md` (define overlay unit + merge strategy + handling local customizations)
- [x] T017 [US3] Add a post-upgrade validation checklist in `README.md` that confirms:
  - `spec-template.md` still contains **Product Context**
  - `plan-template.md` still contains the **Constitution Check** gates
  - `tasks-template.md` still prompts for KPI instrumentation vs explicit deferral

**Checkpoint**: Upgrade guidance is copy/pasteable and verifiable

---

## Phase N: Polish & Cross-Cutting Concerns

**Purpose**: Quality pass across all doc outputs

- [x] T018 [P] Run a link/path sanity pass across `README.md` (all local paths referenced exist; Spec‑Kit link is correct)
- [x] T019 Ensure `README.md` has no placeholders, no contradictory instructions, and consistent formatting (code fences + headings)
- [x] T020 [P] Ensure generated feature docs remain consistent: `specs/001-prodkit-layer-readme/spec.md`, `plan.md`, `quickstart.md`

---

## Dependencies & Execution Order

### Phase Dependencies

- **Setup (Phase 1)**: No dependencies — can start immediately
- **Foundational (Phase 2)**: Depends on Setup completion — blocks all user-story work
- **User Stories (Phase 3+)**: Depend on Foundational completion
  - Stories are mostly sequential because they edit the same `README.md`
- **Polish (Final Phase)**: Depends on completing desired user stories

### User Story Dependencies

- **US1 (P1)**: Must complete before considering the README “done” (core onboarding)
- **US2 (P2)**: Can follow US1; overlaps in the README but is conceptually independent
- **US3 (P3)**: Depends on having the overlay file set defined (Phase 2) and onboarding content (US1)

---

## Parallel Example: Documentation checks

```bash
# Parallelizable checks (different files):
Task: "Validate README-referenced paths exist in repo (`README.md` + filesystem checks)"
Task: "Ensure quickstart.md matches README overlay steps (`specs/001-prodkit-layer-readme/quickstart.md`)"
Task: "Review constitution alignment (`.specify/memory/constitution.md` vs README claims)"
```

---

## Implementation Strategy

### MVP First (User Story 1 Only)

1. Complete Phase 1: Setup
2. Complete Phase 2: Foundational
3. Complete Phase 3: User Story 1
4. **STOP and VALIDATE**: Follow the README end-to-end on a clean Spec‑Kit repo

### Incremental Delivery

1. Deliver US1 onboarding
2. Add US2 explanation + canonical artifacts
3. Add US3 upgrade guidance + validation checklist

---

## Notes

- This is a documentation-only feature; tasks focus on **copy/pasteable** steps and **consistency**
  across README + feature docs.
