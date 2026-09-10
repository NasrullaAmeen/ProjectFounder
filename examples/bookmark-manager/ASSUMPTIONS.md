# Assumptions

> **In plain terms:** these are reasonable guesses this project is running with because `idea.md` doesn't say otherwise. Written by `workflows/brainstorm.md`'s `discover` step (§ 7.2 Discovery Engine) against `examples/bookmark-manager/idea.md`.

| # | Assumption | Question it resolves | Confidence |
|---|---|---|---|
| A1 | Primary users are people doing ongoing research/knowledge work who save links to retrieve later by meaning, not just by title — not casual one-off link-sharers. | Who are the primary users? | MEDIUM — inferred from "semantic search" + organization/collections being core to the idea, not stated directly |
| A2 | Authentication is required for the hosted/cloud offering (to scope each user's own bookmarks), but not necessarily for a single-user self-hosted instance. | Is authentication required? | MEDIUM — inferred from "sync" across web/PWA/extension implying an identity concept for the hosted path; self-hosting's single-tenant case doesn't need one the same way |

## Conventions

- An assumption graduates to a `CONSTRAINTS.md` entry once it's confirmed as a hard rule, or to `OPEN-QUESTIONS.md` if it turns out to need resolving rather than just tracking (see `docs/ASSUMPTIONS.md`'s own convention in the ProjectFounder repo, applied here to a downstream project).
