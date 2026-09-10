# Open Questions

> **In plain terms:** things `idea.md` genuinely doesn't answer and that materially change scope or architecture — unlike `ASSUMPTIONS.md`, these aren't safe to just guess at. Written by `workflows/brainstorm.md`'s `discover` step (§ 111) against `examples/bookmark-manager/idea.md`.

| # | Question | Status | Blocks |
|---|---|---|---|
| Q1 | Should AI (semantic search / summaries) run locally or via a cloud provider? Affects both the "free" constraint (API cost) and the self-hosting story (a cloud-only AI dependency undercuts self-hosting's value). Also covers Gap Analysis's "AI cost"/"AI privacy" categories (§ 123 Step 8) — see `FEATURES.md`. | `open` | Architecture (Phase 3) and Budget (Phase 5), once built |
| Q2 | Is the browser extension required for MVP, or a later-tier feature? `idea.md` lists it alongside web app and PWA with no MVP scoping stated. | `resolved` — tiered MVP by `workflows/requirements.md`'s Feature Discovery step; see `FEATURES.md` | — |

## Conventions

- Move a row to `resolved` once answered, same convention as this repo's own `docs/OPEN-QUESTIONS.md`.
- A `blocking` question must name what it blocks; an `open` one may not block anything yet.
