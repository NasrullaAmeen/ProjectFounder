# Tasks

This is ProjectFounder's own build backlog — tracking work on the repo you're reading. It is **not** the `TASKS.md` artifact ProjectFounder generates for a downstream project (see `ProjectFounder-idea.md` § 91); that one lives at `output/<project>/TASKS.md` and is produced by the Task Engine, not maintained by hand.

Status values: `todo`, `in-progress`, `done`, `deferred`.

## Spec (`ProjectFounder-idea.md`)

- [x] `done` — Meta-research on improving ProjectFounder (blogs/GitHub/HN/Reddit) — `docs/research/2026-09-08-projectfounder-deep-research.md`.
- [x] `done` — § 163.1 Delta-spec / change-scoped artifact mode amendment.
- [x] `done` — § 163.2 Explore-before-design amendment for non-`CREATE` intents.
- [x] `done` — § 163.3 Human-readable plain-language artifact tier amendment.
- [x] `done` — § 163.4 Executable-vs-judged validation amendment.
- [x] `done` — Created this repo's own instance of spec § 88 Core Project Artifacts (the subset with real content today): `docs/DECISIONS.md`, `docs/ASSUMPTIONS.md`, `docs/CONSTRAINTS.md`, `docs/NON-GOALS.md`, `docs/OPEN-QUESTIONS.md`, `docs/LIMITATIONS.md`, `docs/REFERENCES.md` — see `docs/DECISIONS.md` D004.
- [ ] `todo` — P1 research recommendations not yet turned into spec amendments: context persistence across sessions (Memory Engine, § 23), anti-drift loop (Feedback/Validation engines).
- [ ] `todo` — P2 research recommendations: "actions not phases" wording for the Workflow Engine (§ 20), retrospective/feedback step at end of lifecycle (§ 25).

## Phase 0 — Foundation (spec § 140)

Not started. Blocked on a stack decision (language/framework/package manager) — per `AGENTS.md`, this must be surfaced as a Decision Engine (§ 34) choice, not picked unilaterally.

- [ ] `todo` — Decide implementation stack (language, package manager, test runner).
- [ ] `todo` — Project model + `PROJECT.yaml` manifest (§ 120).
- [ ] `todo` — Schema validation loader for `schemas/*.schema.yaml` (currently empty stubs).
- [ ] `todo` — Configuration/policy loader for `config/*.yaml` (currently empty stubs).
- [ ] `todo` — Project state + lifecycle (§ 29, § 25).

## Phases 1–8

Not started — see `ProjectFounder-idea.md` § 140 for the full phase list (Intelligence Core → Research → Architecture → AI/Agents → Budget/Business → Documentation → Validation → Implementation Planning). Do not jump ahead of Phase 0 (`AGENTS.md` "Follow the phase order").

## Conventions

- Add new tasks under the phase/section they belong to; don't create a flat undifferentiated list.
- When a task lands, move it to `done` in the same commit/PR that completes it — don't batch changelog/task updates separately from the work.
- If a task reveals the spec is wrong or incomplete, fix the spec first (with a called-out amendment, see § 163 for the pattern) — then do the task.
