# Notes: running workflows/new-project.md against a genuinely ambiguous intent

This is the third exercise of `workflows/new-project.md`, and the one `examples/notes-app-extend/NOTES.md`'s own takeaway flagged as untried: every prior example (`examples/bookmark-manager/` — `CREATE`; `examples/notes-app-extend/` — `EXTEND`) had a single, unambiguous intent classification. This idea was invented specifically to break that pattern.

## What worked

- Classification (`types`) itself was easy and mostly empty — `product: [Internal]`, `application: [Web]`, `deployment: [Self-Hosted]`, with `technical` and `ai` both legitimately empty (§ 28: "zero, one, or several are valid"). No `other` escape hatch needed this time; not every example has to exercise every prior amendment.
- `mode` was left blank, same judgment call as both prior examples.

## What broke: intent had no escalation path when it was the ambiguous thing, not `types`

The idea text — "I want to rebuild it with a modern frontend and a redesigned schema, but keep the existing ledger engine and reconciliation logic exactly as they are" — has a real claim on three of § 27's fourteen values at once:

- `REBUILD` — "I want to rebuild it" is close to verbatim in the idea.
- `MIGRATE` — porting validated business logic onto a new stack while preserving its behavior is the textbook shape of a migration.
- `EXTEND` — nothing new is being added; the ask could be read as "keep what works, replace what doesn't," which is closer to extension than a ground-up rebuild.

The existing escalation contract (`agents/project-architect.md`, before this exercise) only had two rules: "classification ambiguous across two or more values in the same dimension" (which is about `types`, an array field — the § 163.5 `other` pattern lets it record several plausible values without picking one) and "intent is not `CREATE`" (which assumes `intent` has already resolved to some single value). Neither rule says what to do when `intent` *itself* is the ambiguous thing. And because `schemas/project.schema.yaml` defines `intent` as a single string enum (not an array like `types`), there was no schema-compliant way to "record all plausible values" the way § 28 ambiguity is handled — the agent's only options were to guess silently (forbidden by `AGENT.md`'s "surface uncertainty" rule) or block with no defined recovery path.

This is exactly the gap `examples/notes-app-extend/NOTES.md` predicted: "the escalation rule assumes intent classification is a single clean answer."

## Fixed: § 163.13 Intent Ambiguity Escalation

Added a third escalation rule to `agents/project-architect.md` (and the corresponding amendment, `ProjectFounder-idea.md` § 163.13): when intent is ambiguous across two or more § 27 values, pick the single closest-fit value for `intent` (it stays single-valued — this is deliberately *not* the § 163.5 `other` pattern, which only applies to `types`), and record the rejected candidates plus the reasoning in the project's `OPEN-QUESTIONS.md` (§ 111) instead of silently resolving it. No schema change — `intent` keeps its existing single-valued shape; the ambiguity itself belongs in `OPEN-QUESTIONS.md`, which already exists for exactly this. See `docs/DECISIONS.md` D010.

## This example's own resolution

Per the new rule, `intent: MIGRATE` was chosen as the closest fit, with `REBUILD` and `EXTEND` recorded as rejected candidates:

- Rejected `REBUILD`: a from-scratch rebuild would imply the ledger engine and reconciliation logic get redone too — the idea explicitly rules that out.
- Rejected `EXTEND`: nothing new is being added to the existing system; the frontend and schema are being replaced outright, not added to.
- Selected `MIGRATE`: the ask is precisely "port proven behavior onto a new stack without changing that behavior" — new frontend, new schema, same validated core logic underneath.

Following the § 163.13 rule to the letter would put this reasoning in the project's own `OPEN-QUESTIONS.md`. This worked example doesn't have one — per `docs/DECISIONS.md` D004, these `examples/` directories don't instantiate a full § 88 Core Project Artifact set, only `idea.md` / `PROJECT.yaml` / `NOTES.md` — so it's recorded here instead, in `NOTES.md`'s usual role as this repo's stand-in for a real downstream project's open-question log. A real ProjectFounder run against a real project would write this into that project's `OPEN-QUESTIONS.md`, not skip it.

## Takeaway

Same pattern as both prior exercises: the capture/classify/validate mechanics held up fine, and the real gap was upstream in the escalation *contract*, not a bug in the workflow's own procedure. `docs/TASKS.md`'s specific "try this" case is now exercised; no further untried classification-ambiguity shape is currently flagged.
