# Notes: running workflows/new-project.md against a non-CREATE idea

This is the second exercise of `workflows/new-project.md`, this time specifically to stress-test the § 163.2 Explore branch — every prior run (`examples/bookmark-manager/`) used a `CREATE`-intent idea, so the non-`CREATE` path had never actually been walked.

## What worked

- Recognizing the idea as non-`CREATE` was unambiguous: "I already have a working... app... want to extend it... without migrating off it or rebuilding it" maps cleanly to `EXTEND` (§ 27) rather than `IMPROVE` (which would fit better if the ask were "make existing features better" rather than "add new capabilities").
- `agents/project-architect.md`'s escalation rule ("intent is not CREATE -> do not proceed to Discovery, hand off to Explore first") fired correctly and matched what `workflows/new-project.md` already says in its Classify step.
- The § 163.5 `other` escape hatch got real use again: "AI-powered auto-tagging" doesn't match any of the `ai` dimension's 8 enumerated values, so it went into `other.ai: ["Auto-tagging"]` rather than being force-fit into the closest value (`AI Skill`, used for the enumerated slot) or dropped.
- `mode` was left blank, same judgment call as the first example — no mode value fits "currently exploring" any better than it fits "currently a blank idea," so this isn't a gap, just an unset field until real work starts.

## What broke: § 163.2's EXPLORE step had no lifecycle state to land on

Trying to represent "this project is now in the Explore step" surfaced a real gap: § 25's lifecycle diagram (before this exercise) went `CLASSIFIED -> DISCOVERY` directly — no state existed between them. That left three bad options for a non-`CREATE` project: stay at `CLASSIFIED` (stale — classification is actually done), jump to `DISCOVERY` (directly contradicts § 163.2's own "do not proceed to Discovery" instruction), or use a value like `EXPLORING` that didn't exist in the schema/config enum and would fail validation.

## Fixed: § 163.12 Explore Needs a Lifecycle State

Added `EXPLORING` to § 25's lifecycle, between `CLASSIFIED` and `DISCOVERY`, with `CLASSIFIED`'s next state chosen by the project's own `intent` (non-`CREATE` → `EXPLORING`, `CREATE` → `DISCOVERY`). Synced into `config/lifecycle.yaml` and `schemas/project.schema.yaml`. See `docs/DECISIONS.md` D009.

This example's own `PROJECT.yaml` still stops at `lifecycle: CLASSIFIED`, not `EXPLORING` — `workflows/new-project.md` only implements capture/classify/validate (Phase 0), and advancing the lifecycle value to `EXPLORING` would be claiming Explore has started when nothing has actually run. The fix makes `EXPLORING` a valid *target* for whichever future workflow implements Explore (Phase 1/2), not something this workflow sets itself.

## Takeaway

Same pattern as the first exercise: the capture/classify/validate mechanics held up, and the real gap was upstream in the spec (a diagrammed step with no backing state), not a bug in the workflow's own procedure. Worth noting for next time: every worked example so far has used a small, low-ambiguity idea — a genuinely ambiguous intent (e.g. "rebuild my app but keep some of the old code") hasn't been tried yet and might surface a different kind of gap (the escalation rule assumes intent classification is a single clean answer).
