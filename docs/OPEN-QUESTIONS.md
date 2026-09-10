# Open Questions

> **In plain terms:** these are things nobody has decided yet. Unlike `ASSUMPTIONS.md` (things quietly relied on), these are known gaps that someone needs to actively resolve.

Per `ProjectFounder-idea.md` § 111: "unknown information should become OPEN-QUESTIONS.md... questions may block readiness." Status values: `open`, `blocking`, `resolved`.

| # | Question | Status | Blocks |
|---|---|---|---|
| Q1 | What language/framework/package manager/test runner implements Phase 0 (§ 140)? | `resolved` — agent-executed, no code for now; see `docs/DECISIONS.md` D005 | — |
| Q2 | Should `docs/TASKS.md` (this repo's own backlog) eventually be replaced by a real Task Engine instance once one exists, or stay hand-maintained permanently since it tracks meta-work, not project work? | `open` | Nothing yet |
| Q3 | P1 research recommendations (context persistence via Memory Engine § 23; anti-drift loop via Feedback/Validation) haven't been turned into spec amendments yet. | `resolved` — § 163.6 (session context persistence) and § 163.7 (anti-drift detection loop); see `docs/DECISIONS.md` D007 | — |
| Q4 | P2 research recommendations. All four items (not just the two originally logged here) — "actions not phases" (§ 20), retrospective lifecycle step, autonomy as a project setting, evidence-forward positioning. | `resolved` — § 163.8, § 163.9, § 163.10, § 163.11; see `docs/DECISIONS.md` D008 (§ 163.11 is tracked-not-acted-on by design) | — |
| Q5 | § 163.1's `delta` mode introduces `changes/<change-id>/` and an `archive` step — what triggers archive (human command, automatic on approval, scheduled)? Not yet specified. | `open` | Phase 2+ (Change-Impact Engine implementation) |
| Q6 | § 163.2's Explore step reuses the Research Engine with `source: codebase` — does it need its own skill under `skills/`, or is it a parameter to the existing `research` skill? | `open` | Phase 1/2 (Research Engine implementation) |
| Q7 | Now that `docs/` exists for this repo's own artifacts, should `templates/` gain a matching "meta" template category, or do these docs stay hand-written since they're about ProjectFounder itself, not a generated project? | `open` | Nothing yet |
| Q8 | `config/lifecycle.yaml`'s transition table (§ 25) is strictly linear, exactly as diagrammed. The spec doesn't say whether a project can loop back or archive early from a non-terminal state. | `partially resolved` — § 163.9 adds `EVOLVING -> RESEARCHING` (the one loop-back § 124 actually diagrams). Still open for any other state: e.g. a failed `VALIDATING` → `SPECIFYING`, or early exit to `ARCHIVED` from a non-terminal state — neither is diagrammed anywhere in the spec | `workflows/new-project.md` only reaches `CLASSIFIED`, so not blocking yet |
| Q9 | § 123's own worked classification (Step 3) uses labels — "Search," "Data Platform," bare "AI," "Semantic Search" — that aren't in § 28's taxonomy. | `resolved` — § 163.5 adds a `types.other.<dimension>` free-text field; see `docs/DECISIONS.md` D006 | — |
| Q10 | § 163.14 lets a project reach `RESEARCHING` two ways — directly from `DISCOVERY`, or via `SCOPED` (Gap Analysis/Feature Discovery/Requirements first). If `RESEARCHING` is entered directly, should `DESIGNING` still require `SCOPED`'s output (`REQUIREMENTS.md`) to exist first, given `agents/architecture-agent.md` already says it designs "from validated requirements"? | `resolved` — yes, always; it's a precondition on the DESIGNING/Architecture action, not a lifecycle-state distinction; see § 163.15 and `docs/DECISIONS.md` D014 | — |

## Conventions

- Move a row to `resolved` (don't delete it) once answered, and add the resolution as a `DECISIONS.md` entry — this file tracks that a question existed, the decision log tracks what was decided.
- A `blocking` question must name what it blocks; an `open` one may not block anything yet.
