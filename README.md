# Prod‑Kit

Prod‑Kit is a **product-definition and delivery framework** built on top of GitHub’s
[Spec‑Kit](https://github.com/github/spec-kit). It preserves Spec‑Kit’s workflow, commands, and
mental model, while layering in structured product thinking so teams can move from
idea → product clarity → execution without losing context.

- **Spec‑Kit answers**: “What are we building?”
- **Prod‑Kit answers**: “Why this product, for whom, and how will we know it worked?”

## Table of Contents

- What you get
- Add Prod‑Kit on top of Spec‑Kit (overlay)
- Canonical product artifacts (what to add to your repo)
- Workflow (what changes vs what stays the same)
- Governance
- Upgrading (staying aligned with upstream Spec‑Kit)

## What you get

Prod‑Kit adds:

- A **Product Constitution** concept (durable truths that evolve slowly)
- **Product gates** that make “purpose, scope, KPIs, workflows” first-class alongside specs
- **Traceability** from strategy → product intent → specs → delivery → KPIs
- A recommended **artifact structure** for company, product, competition, KPIs, workflows, roadmap

Prod‑Kit does **not** replace Spec‑Kit phases; it augments them.

## Add Prod‑Kit on top of Spec‑Kit (overlay)

### Prerequisite: initialize Spec‑Kit in your project

In your target repo, install **Specify CLI** (from the Spec‑Kit repo) and initialize Spec‑Kit.

#### Option 1: Persistent install (recommended)

```bash
uv tool install specify-cli --from git+https://github.com/github/spec-kit.git
specify init . --ai claude
```

To upgrade later:

```bash
uv tool install specify-cli --force --from git+https://github.com/github/spec-kit.git
```

#### Option 2: One-time usage (no install)

```bash
uvx --from git+https://github.com/github/spec-kit.git specify init . --ai claude
```

If you already ran `specify init`, you can skip this step.

### Overlay step: copy Prod‑Kit templates and constitution

Copy these files from this `prod-kit` repo into your Spec‑Kit project (same paths):

- `.specify/memory/constitution.md` (Prod‑Kit Constitution; merge if you already have one)
- `.specify/templates/spec-template.md` (adds mandatory **Product Context**)
- `.specify/templates/plan-template.md` (adds **Constitution Check** gates)
- `.specify/templates/tasks-template.md` (adds KPI instrumentation guidance)
- `.claude/commands/*.md` (optional; only if you want the command guidance alongside Claude)

After the overlay, your existing Spec‑Kit commands remain the same (`/speckit.*`), but the templates
and gates will now require product context and traceability.

## Canonical product artifacts (what to add to your repo)

Prod‑Kit expects a product-definition layer alongside feature specs. Default structure:

```text
company/
  profile.md              # company identity, vision, mission, strategic goals

product/
  constitution.md         # durable product truths (vision, ICP, value, success metrics)

competition/
  landscape.md            # competitors, differentiation, positioning notes

kpis/
  kpis.md                 # KPI definitions (activation/engagement/retention/expansion/TTV)
  dashboard.md            # dashboard link + ownership + review cadence (if applicable)

workflows/
  users.md                # personas, roles/permissions
  workflows.md            # 2–3 primary workflows + key edge cases
  technical-workflows.md  # system interactions/data flows/auth/permissions (when needed)

roadmap/
  roadmap.md              # outcome-based milestones, dependencies, trade-offs
```

Minimum viable setup to start using Prod‑Kit:

- `product/constitution.md`
- `kpis/kpis.md`
- `workflows/workflows.md`

## Quickstart: first product with Prod‑Kit

1. Create (or draft) your durable product truths:

   - `product/constitution.md`
   - `kpis/kpis.md`
   - `workflows/workflows.md`

2. Establish project governance (this repo’s constitution drives the gates):

```text
/speckit.constitution
```

3. Create your first spec (now includes mandatory Product Context):

```text
/speckit.specify <describe the feature in plain language>
```

4. Continue with the normal Spec‑Kit flow:

```text
/speckit.plan <tech stack + constraints>
/speckit.tasks
/speckit.implement
```

## Workflow (what changes vs what stays the same)

- **Clarify (augmented)**: you MUST make purpose explicit (who/why/why now/success) and record any
  new durable truths into the Product Constitution.
- **Specify (enhanced)**: specs MUST include Product Context + bounded scope + link to KPIs/workflows.
- **Plan (gated)**: plans MUST pass the Constitution Check (product constitution exists, traceability,
  instrumentation decision recorded).
- **Tasks (traceable)**: tasks remain grouped by user story and MUST include KPI instrumentation tasks
  (or explicit deferral + trigger).

## Governance

The non‑negotiable principles and required artifacts live in:

- `.specify/memory/constitution.md` (Prod‑Kit Constitution)

If you change templates/gates, update the constitution and keep them in sync.

## Upgrading (staying aligned with upstream Spec‑Kit)

Prod‑Kit is an overlay. Upgrades happen in **two layers**:

1) Upgrade **Spec‑Kit / Specify CLI** (upstream)
2) Re-apply/upgrade the **Prod‑Kit overlay file set**

### Upgrade Specify CLI (Spec‑Kit)

```bash
uv tool install specify-cli --force --from git+https://github.com/github/spec-kit.git
```

### Upgrade Spec‑Kit templates/commands in your repo

In a branch, refresh upstream Spec‑Kit templates (this may overwrite local edits):

```bash
specify init . --force --ai claude
```

Then re-apply the Prod‑Kit overlay file set (next section).

### Upgrade the Prod‑Kit overlay (this repo)

Re-apply/merge these overlay files into your Spec‑Kit project (same paths):

- `.specify/memory/constitution.md` (merge; keep your product-specific content)
- `.specify/templates/spec-template.md`
- `.specify/templates/plan-template.md`
- `.specify/templates/tasks-template.md`

Optional:

- `.claude/commands/*.md`

If you’ve customized templates, upgrade by **merging** (not overwriting) and keep a small diff so
future upgrades are repeatable.

### Post-upgrade validation checklist

Validate that Prod‑Kit gates are still present:

- `/.specify/templates/spec-template.md` still contains mandatory **Product Context**
- `/.specify/templates/plan-template.md` still contains the **Constitution Check** gates
- `/.specify/templates/tasks-template.md` still prompts for KPI instrumentation vs explicit deferral

