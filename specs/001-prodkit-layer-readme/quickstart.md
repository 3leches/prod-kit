# Quickstart: Add Prod‑Kit on top of Spec‑Kit

## 1) Install Specify CLI (Spec‑Kit)

```bash
uv tool install specify-cli --from git+https://github.com/github/spec-kit.git
```

Optional one-time usage:

```bash
uvx --from git+https://github.com/github/spec-kit.git specify init . --ai claude
```

## 2) Initialize Spec‑Kit in your repo

```bash
specify init . --ai claude
```

## 3) Overlay Prod‑Kit

Copy/merge these paths from the `prod-kit` repo into your Spec‑Kit project:

- `.specify/memory/constitution.md`
- `.specify/templates/spec-template.md`
- `.specify/templates/plan-template.md`
- `.specify/templates/tasks-template.md`

Optional (agent guidance docs):

- `.claude/commands/*.md`

## 4) Run the normal Spec‑Kit workflow (now with Prod‑Kit gates)

```text
/speckit.constitution
/speckit.specify <describe the feature>
/speckit.plan <tech stack + constraints>
/speckit.tasks
/speckit.implement
```

