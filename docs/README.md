# Docs

This folder holds documentation about **this repository's own development** — the meta layer around building ProjectFounder — as opposed to the artifacts ProjectFounder generates for a downstream project (those land in `output/<project>/`, see `output/README.md`).

## Contents

- [`CHANGELOG.md`](./CHANGELOG.md) — notable changes to this repo, release by release.
- [`TASKS.md`](./TASKS.md) — this repo's own build backlog (spec amendments, Phase 0–8 implementation work). Not the `TASKS.md` artifact ProjectFounder generates per project (spec § 91).
- [`DECISIONS.md`](./DECISIONS.md) — real decisions made building this repo, using the Decision Engine record shape (spec § 34).
- [`ASSUMPTIONS.md`](./ASSUMPTIONS.md) — unproven premises the design currently relies on.
- [`CONSTRAINTS.md`](./CONSTRAINTS.md) — hard rules the design must not break (traceable to spec sections or `AGENTS.md`/`AGENT.md`).
- [`NON-GOALS.md`](./NON-GOALS.md) — what v0.1 deliberately does not attempt (spec § 138–139).
- [`OPEN-QUESTIONS.md`](./OPEN-QUESTIONS.md) — unresolved questions that may block readiness (spec § 111).
- [`LIMITATIONS.md`](./LIMITATIONS.md) — what doesn't work yet, stated plainly (spec § 110).
- [`REFERENCES.md`](./REFERENCES.md) — index of external sources cited in the spec or a decision.
- [`research/`](./research/) — meta-research: evidence and synthesis about how to improve ProjectFounder itself, not research ProjectFounder produces for a downstream project.

These seven files (`DECISIONS.md` … `REFERENCES.md`) are this repo's own instance of the spec's Core Project Artifacts (§ 88) — the subset with real content today. See `DECISIONS.md` D004 for why the rest of § 88 (`TECH-STACK.md`, `ARCHITECTURE.md`, `BUDGET.md`, `ROADMAP.md`, `REQUIREMENTS.md`, `FEATURES.md`, …) isn't generated yet.

## Conventions

- Keep this README's contents list in sync when a file is added or removed here.
- Don't put project-generated artifacts (the ones ProjectFounder produces when run against an idea) in this folder — those belong under `output/<project>/`.
