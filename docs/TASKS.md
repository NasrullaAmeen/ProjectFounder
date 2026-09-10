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
- [x] `done` — § 163.6 Session context persistence amendment (`MEMORY.md`, required session-bootstrap step).
- [x] `done` — § 163.7 Anti-drift detection loop amendment (`drift_status` on every canonical artifact, wired to the Feedback Engine).
- [x] `done` — § 163.8 Actions, Not Phases (Workflow Engine reframed as invokable actions with preconditions).
- [x] `done` — § 163.9 Retrospective lifecycle step (`EVOLVING -> RESEARCHING`, synced into `config/lifecycle.yaml`).
- [x] `done` — § 163.10 Autonomy as a project setting (`default_autonomy`, synced into `schemas/project.schema.yaml`, `templates/core/PROJECT.yaml`, `examples/bookmark-manager/PROJECT.yaml`, `workflows/new-project.md`).
- [x] `done` — § 163.11 Evidence-forward positioning — logged as tracked-not-acted-on by design (no real run to point to yet).

## Phase 0 — Foundation (spec § 140)

Complete for its declared scope, agent-executed per `docs/DECISIONS.md` D005 (no code, until an engine needs deterministic logic beyond what an agent can do by reading files). Exercised twice end-to-end: `examples/bookmark-manager/` (`CREATE` intent) and `examples/notes-app-extend/` (`EXTEND` intent, exercising the § 163.2 Explore branch).

- [x] `done` — Decide implementation stack — resolved as agent-only for now (D005).
- [x] `done` — Project model + `PROJECT.yaml` manifest (§ 120): `schemas/project.schema.yaml` fleshed out, `templates/core/PROJECT.yaml` fillable template added.
- [x] `done` — Project classification taxonomy (§ 28): `config/project-types.yaml` fleshed out.
- [x] `done` — Lifecycle state machine (§ 25): `config/lifecycle.yaml` fleshed out (linear, per the spec's diagram — see `docs/OPEN-QUESTIONS.md` Q8 for loop-back/early-archive, not yet resolved).
- [x] `done` — First real agent contract: `agents/project-architect.md` fleshed out with concrete inputs/outputs/permissions/escalation.
- [x] `done` — First real workflow + command: `workflows/new-project.md` (capture → classify → validate, stops at `CLASSIFIED`) and `commands/new-project.md`.
- [ ] `todo` — "Schema validation loader" / "Configuration/policy loader" as originally scoped (a program that reads `schemas/*.schema.yaml` / `config/*.yaml` and validates automatically) — deliberately not built; Phase 0 validation is agent-judged per D005. Revisit if/when this stops scaling (`docs/OPEN-QUESTIONS.md` Q2).
- [x] `done` — Exercised `workflows/new-project.md` end-to-end against the § 123 bookmark-manager idea: `examples/bookmark-manager/`. Found and fixed a real gap (missing `created_at`/`updated_at` in the schema/template). Found and fixed a second gap via § 163.5 (classification escape hatch, `docs/DECISIONS.md` D006) — see `examples/bookmark-manager/NOTES.md`.
- [x] `done` — Stress-tested the § 163.2 Explore branch with a second, non-`CREATE` example: `examples/notes-app-extend/`. Found and fixed a real gap — § 25's lifecycle had no state for the Explore step — via § 163.12 (`docs/DECISIONS.md` D009) — see `examples/notes-app-extend/NOTES.md`.
- [x] `done` — Tried a genuinely ambiguous intent ("rebuild my app but keep some of the old code"): `examples/ambiguous-intent/`. Found and fixed a real gap — the escalation contract had no rule for `intent` itself being ambiguous (only for `types` ambiguity) — via § 163.13 (`docs/DECISIONS.md` D010) — see `examples/ambiguous-intent/NOTES.md`.

## Phase 1 — Intelligence Core (spec § 140)

Covers Discovery, Brainstorm, Classification, Requirements, Feature Discovery, Gap Analysis. Classification (§ 28) was already built in Phase 0 (`agents/project-architect.md`) — nothing further needed there. Discovery + Brainstorm are the first slice built, since § 123's own journey runs them (Steps 4–5) immediately after Classification, without needing Research (Phase 2) first; Requirements/Feature Discovery/Gap Analysis (§ 123 Steps 8–10) run *after* Research in that same journey, so their contracts are deferred to a follow-up slice rather than built (and left unexercisable) in this one.

- [x] `done` — First real Discovery/Brainstorm agent contracts: `agents/discovery-agent.md`, `agents/brainstorm-agent.md`, fleshed out with concrete inputs/outputs/permissions/escalation, plus `skills/discovery/SKILL.md` (new) and `skills/brainstorm/SKILL.md` (fleshed out from its Phase 0 stub).
- [x] `done` — First real Phase 1 workflow + command: `workflows/brainstorm.md` (precondition-check → discover → brainstorm → advance lifecycle to `DISCOVERY`) and `commands/brainstorm.md`. Named `brainstorm` per § 143's own "Initial Workflows" list (which names `brainstorm`, not a separate `discovery` workflow).
- [x] `done` — Decided where Brainstorm's raw candidate list lives: reused `FEATURES.md` (§ 88) marked explicitly draft/uncategorized, rather than a new `BRAINSTORM.md` artifact — see `docs/DECISIONS.md` D011.
- [x] `done` — Exercised `workflows/brainstorm.md` end-to-end against `examples/bookmark-manager/` (the same `CLASSIFIED`, `CREATE`-intent project Phase 0 founded) — see `examples/bookmark-manager/NOTES.md` for what running it surfaced.
- [x] `done` — Fleshed out Requirements, Feature Discovery, and Gap Analysis agent/skill contracts: `agents/requirements-agent.md` (new), `agents/gap-analysis-agent.md` (new), `agents/product-agent.md` (fleshed, Feature Discovery half only), `skills/requirements/`, `skills/feature-discovery/`, `skills/gap-analysis/` (all fleshed from blank stubs). Corrected the dependency order while doing so: Brainstorm → Gap Analysis (appends missed features) → Feature Discovery (tiers the full list into MVP/V1/V2/Future) → Requirements (writes requirements against the tiered list) — matching § 123 Steps 5/8/9/10, not an arbitrary order.
- [x] `done` — Decided where Gap Analysis's findings live: routed into `FEATURES.md`/`OPEN-QUESTIONS.md` by category, no new `GAPS.md` artifact — see `docs/DECISIONS.md` D012.
- [x] `done` — Wired `workflows/requirements.md` (Gap Analysis → Feature Discovery → Requirements) and `commands/requirements.md`, and exercised it end-to-end against `examples/bookmark-manager/`. Not blocked on Research (Phase 2) — both Gap Analysis and Feature Discovery ran on internal signals alone this round; no competitive-positioning tier call actually needed Research to be decidable. Found and fixed a real gap — `DISCOVERY` had no lifecycle state to land on that didn't overclaim Research happened — via § 163.14 (`docs/DECISIONS.md` D013, new `SCOPED` state) — see `examples/bookmark-manager/NOTES.md`.

## Phase 1 — remaining after this slice

- [x] `done` — Resolved `docs/OPEN-QUESTIONS.md` Q10: `DESIGNING` always requires `REQUIREMENTS.md`, regardless of whether `RESEARCHING` was reached via `SCOPED` or directly from `DISCOVERY` — encoded as a precondition on the Architecture action (`agents/architecture-agent.md` escalation), not a new lifecycle state. See § 163.15, `docs/DECISIONS.md` D014.
- [ ] `todo` — Try a Feature Discovery run where a tier call genuinely can't be decided from internal signals alone (needs real competitive research) — every tier call in `examples/bookmark-manager/` was decidable without it, so the "provisional" escalation path (`agents/product-agent.md`) is still unexercised.

## Phases 2–8

Not started — see `ProjectFounder-idea.md` § 140 for the full phase list (Research → Architecture → AI/Agents → Budget/Business → Documentation → Validation → Implementation Planning). Do not jump ahead of Phase 1's remaining items (`AGENTS.md` "Follow the phase order").

## Conventions

- Add new tasks under the phase/section they belong to; don't create a flat undifferentiated list.
- When a task lands, move it to `done` in the same commit/PR that completes it — don't batch changelog/task updates separately from the work.
- If a task reveals the spec is wrong or incomplete, fix the spec first (with a called-out amendment, see § 163 for the pattern) — then do the task.
