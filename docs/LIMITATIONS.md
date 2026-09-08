# Limitations

> **In plain terms:** this is what ProjectFounder cannot actually do yet, stated plainly so nobody assumes more capability than exists. Per § 110: "unknown limitations should not be hidden" — this file exists so none are.

## Nothing executes as code

Phase 0 is implemented as agent-executed contracts, not a program (`docs/DECISIONS.md` D005) — there is no interpreter/runtime, no CLI, and no automated validation. "Implemented" for `project-architect`/`new-project` means a coding agent follows the contract by reading it; nothing here runs unattended.

- 19 of 20 engines in § 7 (Complete Engine Inventory) are specification only — no agent contract or workflow exists for them yet. Only the Project Engine (§ 7.1) has a working slice (`agents/project-architect.md`, `workflows/new-project.md`).
- `schemas/*.schema.yaml` are still empty stubs (`properties: {}`) except `project.schema.yaml` — nothing validates against any of them mechanically; even `project.schema.yaml` is checked by an agent reading it, not a validator.
- `config/*.yaml` are still empty stubs except `lifecycle.yaml` and `project-types.yaml` — no policy is mechanically enforced.
- `checks/`, `resources/` contain only READMEs describing what will eventually live there ("Status: not yet implemented"). `commands/` and `workflows/` now each have one real file (`new-project.md`); everything else planned for them is still just a README list.
- `agents/*.md` (except `project-architect.md`) and all of `skills/*/` are still draft contracts with empty arrays, not runnable prompts/tools.
- `examples/bookmark-manager/` and `examples/notes-app-extend/` both only cover capture + classify — neither Discovery (Phase 1) nor Explore (§ 163.2, Phase 1/2) has ever actually run; `EXPLORING` (§ 163.12) is a defined lifecycle state with no workflow that sets it yet.
- The § 163.5 classification escape hatch (`types.other.<dimension>`) has been exercised twice, both times for at most 2 free-text labels in one dimension — not tested against an idea with no fit at all in a dimension, or many `other` labels at once.
- Both worked examples have unambiguous intent (`CREATE`, `EXTEND`) — a genuinely ambiguous idea (e.g. "rebuild but keep some of the old code") hasn't been tried; `agents/project-architect.md`'s escalation rule assumes classification produces one clean answer per dimension.

## No implementation stack chosen for anything beyond Phase 0's agent-only slice

Q1 (`docs/OPEN-QUESTIONS.md`) is resolved for Phase 0 specifically (agent-only, D005), not for the project as a whole — if/when an engine needs real deterministic logic, the stack question reopens (Q2). Nothing in this repo can currently be run, tested, or built as software; there is no build/test tooling (`AGENTS.md` "this repo has no build/test tooling yet").

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
