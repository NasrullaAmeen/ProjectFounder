# Examples

Worked examples, including the canonical v0.1 user journey (see ProjectFounder-idea.md, Section 123 — Concrete v0.1 User Journey): a free AI-powered bookmark manager with web app, PWA, browser extension, and semantic search.

- [`bookmark-manager/`](./bookmark-manager/) — § 123's idea run through `workflows/new-project.md`, `intent: CREATE` (Phase 0: capture + classify only, stops at lifecycle `CLASSIFIED`). See `bookmark-manager/NOTES.md` for what the exercise found — including a real gap between § 123's own classification and § 28's taxonomy (`docs/OPEN-QUESTIONS.md` Q9, resolved by § 163.5).
- [`notes-app-extend/`](./notes-app-extend/) — an invented non-`CREATE` idea (`intent: EXTEND`), run through the same workflow specifically to exercise the § 163.2 Explore branch. See `notes-app-extend/NOTES.md` — found that § 25's lifecycle had no state for § 163.2's Explore step at all, fixed by § 163.12.
- [`ambiguous-intent/`](./ambiguous-intent/) — an invented idea that plausibly fits three of § 27's intent values at once (`REBUILD`, `MIGRATE`, `EXTEND`), run through the same workflow specifically to stress-test intent classification once it's no longer a clean single answer. See `ambiguous-intent/NOTES.md` — found the escalation contract had no rule for intent ambiguity (only for `types` ambiguity), fixed by § 163.13.

Status: Phase 0 slice populated for a `CREATE` intent, a non-`CREATE` intent, and an ambiguous intent. § 123's later steps (Discovery onward) and § 163.2's Explore step aren't run here since those engines don't exist yet.
