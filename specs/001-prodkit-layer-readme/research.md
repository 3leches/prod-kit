# Phase 0 Research: Prod‑Kit Overlay README

## Decisions

- **Specify CLI install path**: Recommend `uv tool install specify-cli --from git+https://github.com/github/spec-kit.git`
  (persistent install), and include `uvx --from ...` as a one-time alternative.
- **Positioning**: Prod‑Kit is an overlay that augments Spec‑Kit; it MUST not present itself as a fork
  or replacement workflow.
- **Overlay mechanism**: Instruct users to copy a small, explicit set of overlay files into their
  Spec‑Kit repo (constitution + templates), preserving existing `/speckit.*` commands.

## Rationale

- **Mirror Spec‑Kit**: Using the same `uv tool` install flow reduces adoption friction and keeps the
  instructions aligned with Spec‑Kit’s canonical docs.
- **Avoid parallel processes**: Users should keep the same phase model; Prod‑Kit adds gates/artifacts
  to embed product thinking and traceability.

## Alternatives considered

- **Install Specify CLI from this repo**: Rejected. Specify CLI is defined by Spec‑Kit upstream and
  should be installed from `github/spec-kit` to avoid ambiguity.
- **Include example product artifacts in this repo**: Rejected for this feature scope. This repo is
  an overlay toolkit; examples can be a separate feature if desired.

