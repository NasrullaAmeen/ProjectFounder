# Limitations

> **In plain terms:** this is what ProjectFounder cannot actually do yet, stated plainly so nobody assumes more capability than exists. Per § 110: "unknown limitations should not be hidden" — this file exists so none are.

## Nothing executes yet

This is a v0.1 **scaffold** — contracts, schemas, and configuration exist as drafts; no engine, workflow, or orchestration runtime is implemented:

- All 20 engines in § 7 (Complete Engine Inventory) are specification only — no code.
- `schemas/*.schema.yaml` are empty stubs (`properties: {}`) — nothing validates against them yet.
- `config/*.yaml` are empty stubs — no policy is actually enforced.
- `checks/`, `commands/`, `workflows/`, `resources/` contain only READMEs describing what will eventually live there ("Status: not yet implemented").
- `agents/*.md` and `skills/*/` are draft contracts, not runnable prompts/tools.
- `examples/` is not yet populated with the worked bookmark-manager journey (§ 123).

## No implementation stack chosen

Phase 0 (§ 140) hasn't started — see `docs/OPEN-QUESTIONS.md` Q1. Nothing in this repo can currently be run, tested, or built; there is no build/test tooling (`AGENTS.md` "this repo has no build/test tooling yet").

## The spec itself is large and partly untested against reality

- `ProjectFounder-idea.md` is ~4,900 lines of design intent; none of it has been validated by actually running a project through the pipeline end-to-end.
- The § 123 "Concrete v0.1 User Journey" (bookmark manager) is a worked example on paper, not something that has actually been executed.
- § 163's amendments are themselves unimplemented — they change what the spec says should happen, not what currently happens.

## Research currency

- The meta-research in `docs/research/` reflects one research pass on 2026-09-08; the SDD tooling landscape moves fast (the research report itself flags this) and may already be stale by the time this is read.
- Only P0 recommendations have been folded into the spec so far; P1/P2 remain open (`docs/OPEN-QUESTIONS.md` Q3–Q4).

## Conventions

- A limitation here should describe what doesn't work today, not what's philosophically out of scope (that's `NON-GOALS.md`) or what's unresolved (that's `OPEN-QUESTIONS.md`).
- Remove an entry only when the limitation is actually fixed — not when it becomes inconvenient to keep listed.
