# Open Questions

> **In plain terms:** these are things nobody has decided yet. Unlike `ASSUMPTIONS.md` (things quietly relied on), these are known gaps that someone needs to actively resolve.

Per `ProjectFounder-idea.md` § 111: "unknown information should become OPEN-QUESTIONS.md... questions may block readiness." Status values: `open`, `blocking`, `resolved`.

| # | Question | Status | Blocks |
|---|---|---|---|
| Q1 | What language/framework/package manager/test runner implements Phase 0 (§ 140)? | `blocking` | All Phase 0 work (`docs/TASKS.md`) |
| Q2 | Should `docs/TASKS.md` (this repo's own backlog) eventually be replaced by a real Task Engine instance once one exists, or stay hand-maintained permanently since it tracks meta-work, not project work? | `open` | Nothing yet |
| Q3 | P1 research recommendations (context persistence via Memory Engine § 23; anti-drift loop via Feedback/Validation) haven't been turned into spec amendments yet — should they follow the same § 163.x pattern, or wait until Phase 1/2 makes them concrete? | `open` | Nothing yet — noted in `docs/TASKS.md` |
| Q4 | P2 research recommendations ("actions not phases" wording for the Workflow Engine § 20; a retrospective/feedback lifecycle step) — same question as Q3. | `open` | Nothing yet |
| Q5 | § 163.1's `delta` mode introduces `changes/<change-id>/` and an `archive` step — what triggers archive (human command, automatic on approval, scheduled)? Not yet specified. | `open` | Phase 2+ (Change-Impact Engine implementation) |
| Q6 | § 163.2's Explore step reuses the Research Engine with `source: codebase` — does it need its own skill under `skills/`, or is it a parameter to the existing `research` skill? | `open` | Phase 1/2 (Research Engine implementation) |
| Q7 | Now that `docs/` exists for this repo's own artifacts, should `templates/` gain a matching "meta" template category, or do these docs stay hand-written since they're about ProjectFounder itself, not a generated project? | `open` | Nothing yet |

## Conventions

- Move a row to `resolved` (don't delete it) once answered, and add the resolution as a `DECISIONS.md` entry — this file tracks that a question existed, the decision log tracks what was decided.
- A `blocking` question must name what it blocks; an `open` one may not block anything yet.
