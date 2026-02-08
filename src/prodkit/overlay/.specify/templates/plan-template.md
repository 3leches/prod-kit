# Implementation Plan: [FEATURE]

**Branch**: `[###-feature-name]` | **Date**: [DATE] | **Spec**: [link]
**Input**: Feature specification from `/specs/[###-feature-name]/spec.md`

## Constitution Check

*GATE: Must pass before Phase 0 research. Re-check after Phase 1 design.*

Fill these gates from `/.specify/memory/constitution.md` (Prod‑Kit Constitution).

- [ ] **Product Constitution exists**: This feature links to the product’s `product/constitution.*`
      and the constitution includes vision, ICP, value, differentiation, and success metrics.
- [ ] **Purpose is explicit**: The spec answers “who is this for, what problem/value, why now,
      and what does success look like?” (measurable).
- [ ] **Scope is bounded**: In-scope and explicit out-of-scope are stated.
- [ ] **Traceability**: The spec/plan links to the KPIs it moves (`kpis/*`) and the user workflows
      it impacts (`workflows/*`).
- [ ] **Augmentation, not replacement**: Any workflow/tooling changes extend existing Spec‑Kit
      phases rather than inventing a parallel process.
- [ ] **Instrumentation decision recorded**: If KPIs require measurement at GA, instrumentation
      is planned; if deferred, deferral + trigger is documented.

