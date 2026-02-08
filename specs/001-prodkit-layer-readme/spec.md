# Feature Specification: Prod‑Kit Overlay README

**Feature Branch**: `001-prodkit-layer-readme`  
**Created**: 2026-02-08  
**Status**: Draft  
**Input**: Create a readme just like `github/spec-kit` to show users how to add this layer on top
of their Spec‑Kit install.

## Product Context *(mandatory)*

- **Product Constitution**: `.specify/memory/constitution.md` (Prod‑Kit Constitution)
- **ICP / User**: teams already using Spec‑Kit who want stronger product definition + traceability
- **Problem / Value**: users need a clear, copy/pasteable path to layer Prod‑Kit onto Spec‑Kit without
  forking Spec‑Kit’s workflow.
- **Primary KPIs impacted**: Activation (successful setup), Time-to-value (first product constitution +
  spec completed), Engagement (repeat use of augmented gates)

## Clarifications

### Session 2026-02-08

- Q: Ensure there is a upgrade path to upgrade either Spec‑Kit and/or Prod‑Kit → A: README must document
  upgrades for (1) Specify CLI + Spec‑Kit templates/commands and (2) the Prod‑Kit overlay file set, with
  a “merge overlay after upstream updates” approach.

## User Scenarios & Testing *(mandatory)*

<!--
  IMPORTANT: User stories should be PRIORITIZED as user journeys ordered by importance.
  Each user story/journey must be INDEPENDENTLY TESTABLE - meaning if you implement just ONE of them,
  you should still have a viable MVP (Minimum Viable Product) that delivers value.
  
  Assign priorities (P1, P2, P3, etc.) to each story, where P1 is the most critical.
  Think of each story as a standalone slice of functionality that can be:
  - Developed independently
  - Tested independently
  - Deployed independently
  - Demonstrated to users independently
-->

### User Story 1 - Layer Prod‑Kit onto an existing Spec‑Kit project (Priority: P1)

As a user with an existing Spec‑Kit-initialized repository, I want a README that explains how to
add Prod‑Kit as an extension layer so I can start using the Product Constitution and gates without
changing the core Spec‑Kit workflow.

**Why this priority**: Without an onboarding path, Prod‑Kit is hard to adopt and easy to misapply.

**Independent Test**: A new user can follow the README steps and end up with the expected files +
folders, and can successfully run `/speckit.constitution` and `/speckit.specify` using the augmented
templates.

**Acceptance Scenarios**:

1. **Given** a repo already initialized with Spec‑Kit, **When** I follow the README “Add Prod‑Kit
   layer” steps, **Then** I can locate all required artifacts in the documented canonical locations.
2. **Given** the repo after layering, **When** I start a new spec, **Then** the spec template includes
   the mandatory “Product Context” section and I can link it to a product constitution.

---

### User Story 2 - Understand what Prod‑Kit changes (Priority: P2)

As a user, I want a concise explanation of what Prod‑Kit adds (and what it intentionally does not
change) so I can decide whether to adopt it and how to fit it into my workflow.

**Why this priority**: Clear positioning prevents confusion and “parallel process” anti-patterns.

**Independent Test**: A user can answer: what does Prod‑Kit add, which artifacts are new, and which
Spec‑Kit phases remain unchanged.

**Acceptance Scenarios**:

1. **Given** I’m evaluating Prod‑Kit, **When** I read the README overview, **Then** I can clearly
   distinguish “Spec‑Kit: what” vs “Prod‑Kit: why/for whom/how measured”.

---

### User Story 3 - Upgrade and maintenance guidance (Priority: P3)

As a maintainer, I want clear guidance for keeping Prod‑Kit aligned with upstream Spec‑Kit so we
can pull updates without breaking the augmentation layer.

**Why this priority**: Prod‑Kit’s value depends on staying compatible with Spec‑Kit’s workflow.

**Independent Test**: A maintainer can follow an “upgrade” section to update upstream templates and
re-run a small consistency checklist.

**Acceptance Scenarios**:

1. **Given** a new Spec‑Kit template release, **When** I follow the README upgrade steps, **Then** I
   can update while preserving Prod‑Kit gates and canonical artifact structure.

---

[Add more user stories as needed, each with an assigned priority]

### Edge Cases

<!--
  ACTION REQUIRED: The content in this section represents placeholders.
  Fill them out with the right edge cases.
-->

- What happens when a user tries to use Prod‑Kit without adding the canonical directories (missing
  `product/constitution.*`)?
- How does the README guide users who have a non-standard Spec‑Kit layout (e.g., different agent
  command location) without breaking the augmentation principle?
- What happens when users upgrade Spec‑Kit (or Specify CLI) and it overwrites templates that Prod‑Kit
  overlays?
- What happens when users upgrade Prod‑Kit overlay files and their repo has local customizations in
  `.specify/memory/constitution.md` or templates?

## Requirements *(mandatory)*

<!--
  ACTION REQUIRED: The content in this section represents placeholders.
  Fill them out with the right functional requirements.
-->

### Functional Requirements

- **FR-001**: The repository MUST provide a root `README.md` that explains what Prod‑Kit is and how
  it relates to Spec‑Kit.
- **FR-002**: The README MUST include a step-by-step “Add Prod‑Kit layer” section that starts from
  a repo already initialized by Spec‑Kit (`specify init`).
- **FR-003**: The README MUST document Prod‑Kit’s required artifacts and canonical locations
  (company/product/competition/kpis/workflows/roadmap), consistent with `.specify/memory/constitution.md`.
- **FR-004**: The README MUST document how the Spec‑Kit commands remain the primary workflow (no
  fork), and how Prod‑Kit augments them via templates/gates.
- **FR-005**: The README MUST include a minimal quickstart that demonstrates: create product
  constitution → create a spec that links to it → proceed to plan/tasks.
- **FR-006**: The README MUST include an “Upgrading / staying aligned with Spec‑Kit” section that
  describes how to pull upstream changes while preserving Prod‑Kit overlays.
- **FR-007**: The README MUST include a “Upgrading Prod‑Kit overlay” subsection that defines the
  upgrade unit (overlay file set), a merge strategy (update upstream first, then re-apply overlay),
  and a short validation checklist to confirm Prod‑Kit gates are still present post-upgrade.

### Key Entities *(include if feature involves data)*

- **README**: the primary onboarding document describing adoption and usage.
- **Overlay Steps**: the set of copy/pasteable steps that apply Prod‑Kit on top of Spec‑Kit.

## Success Criteria *(mandatory)*

<!--
  ACTION REQUIRED: Define measurable success criteria.
  These must be technology-agnostic and measurable.
-->

### Measurable Outcomes

- **SC-001**: A new user can complete “Add Prod‑Kit layer” setup in under 15 minutes, using only
  the README steps.
- **SC-002**: After setup, a user can create a new spec that includes “Product Context” and links
  to a product constitution without additional guidance.
- **SC-003**: The README contains zero placeholders and zero unresolved clarification markers.
- **SC-004**: A maintainer can follow the README upgrade guidance to (a) upgrade Specify CLI and
  (b) re-apply/merge Prod‑Kit overlay files, and then confirm the three Prod‑Kit template changes
  still exist (Product Context in spec template; Constitution Check gates in plan template; KPI
  instrumentation note in tasks template).
