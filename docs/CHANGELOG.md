# Changelog

All notable changes to this project will be documented in this file.

This changelog tracks ProjectFounder's own development (the repo you're reading), not the artifacts ProjectFounder generates for downstream projects — those get their own `output/<project>/` history.

## [Unreleased]

### Added — third worked example

- `examples/ambiguous-intent/`: an invented idea that plausibly fits three of § 27's intent values at once (`REBUILD`, `MIGRATE`, `EXTEND`), run through `workflows/new-project.md` specifically to try the case `docs/TASKS.md` had flagged as untried — a genuinely ambiguous intent (`idea.md`, `PROJECT.yaml`, `NOTES.md`).

### Fixed

- `agents/project-architect.md`'s escalation contract had no rule for `intent` itself being ambiguous — only for `types` ambiguity (§ 163.5) and for intent already resolved to non-`CREATE`. Found while building the third worked example. Added `ProjectFounder-idea.md` § 163.13 "Intent Ambiguity Escalation": pick the single closest-fit value for `intent` (it stays single-valued, unlike `types`), and record the rejected candidates plus the reasoning in the project's `OPEN-QUESTIONS.md` (§ 111) instead of silently resolving it. Logged as `docs/DECISIONS.md` D010.

### Added — spec

- `ProjectFounder-idea.md` § 163.6 "Session Context Persistence": `MEMORY.md` joins § 88's Core Project Artifacts (scoped to user preferences, implementation discoveries, and lessons learned — not duplicating `DECISIONS.md`/`ASSUMPTIONS.md`/research artifacts), plus a required session-bootstrap step (`PROJECT.yaml`, `MEMORY.md`, `DECISIONS.md`, `OPEN-QUESTIONS.md` read before any engine runs). Resolves the Memory Engine half of `docs/OPEN-QUESTIONS.md` Q3.
- `ProjectFounder-idea.md` § 163.7 "Anti-Drift Detection Loop": generalizes § 37's research freshness enum into a `drift_status` field (`IN_SYNC`/`SUSPECT`/`DRIFTED`/`UNKNOWN`) on every canonical artifact, wired to the Feedback Engine and propagated via the Artifact Dependency Graph (§ 107); Final Quality Gates (§ 135) now check no canonical artifact is `DRIFTED` at R6/R7. Resolves the anti-drift half of Q3.
- Both logged as `docs/DECISIONS.md` D007.

### Added — spec (P2)

- `ProjectFounder-idea.md` § 163.8 "Actions, Not Phases": reframes the Workflow Engine (§ 20) as independently invokable actions with declared `preconditions`, not one locked pipeline — formalizing what `commands/new-project.md`/`workflows/new-project.md` already do.
- § 163.9 "Retrospective as a Lifecycle Reassess Step": wires `EVOLVING -> RESEARCHING` as a legal lifecycle transition, matching § 124's own Continuous Intelligence Loop diagram; partially resolves `docs/OPEN-QUESTIONS.md` Q8. Synced into `config/lifecycle.yaml`.
- § 163.10 "Autonomy as a Project Setting": adds `default_autonomy` (§ 9's L0-L5 scale) to `PROJECT.yaml`. Synced into `schemas/project.schema.yaml`, `templates/core/PROJECT.yaml`, `examples/bookmark-manager/PROJECT.yaml`, and `workflows/new-project.md`.
- § 163.11 "Evidence as the Visible Differentiator": positioning note only, deliberately not acted on until there's a real run to point to.
- Resolves `docs/OPEN-QUESTIONS.md` Q4 in full — logged as `docs/DECISIONS.md` D008, which also notes and corrects an earlier triage gap (two of these four P2 items were dropped when D003 first logged the research findings).

### Added — second worked example

- `examples/notes-app-extend/`: an invented non-`CREATE` idea (`intent: EXTEND`), run through `workflows/new-project.md` specifically to exercise the § 163.2 Explore branch (`idea.md`, `PROJECT.yaml`, `NOTES.md`).

### Fixed

- § 25's lifecycle diagram had no state corresponding to § 163.2's Explore step, going straight from `CLASSIFIED` to `DISCOVERY`. Found while building the second worked example. Added `ProjectFounder-idea.md` § 163.12 "Explore Needs a Lifecycle State" (`EXPLORING`, between `CLASSIFIED` and `DISCOVERY`), synced into `config/lifecycle.yaml` and `schemas/project.schema.yaml`. Logged as `docs/DECISIONS.md` D009.

### Added — Phase 0 (§ 140)

- Resolved the Phase 0 stack decision (`docs/OPEN-QUESTIONS.md` Q1 → `docs/DECISIONS.md` D005): agent-executed contracts, no code, until an engine needs deterministic logic an agent can't do by reading files.
- Fleshed out `schemas/project.schema.yaml` (full `PROJECT.yaml` shape: lifecycle, mode, intent, classification, complexity, readiness, quality/research/documentation depth).
- Fleshed out `config/lifecycle.yaml` (§ 25 lifecycle states + linear transitions) and `config/project-types.yaml` (§ 28 classification taxonomy).
- Fleshed out the `project-architect` agent contract (`agents/project-architect.md`) with concrete inputs, outputs, permissions, and escalation rules.
- Added the first real workflow and command: `workflows/new-project.md` (capture → classify → validate, stops at lifecycle `CLASSIFIED`) and `commands/new-project.md`.
- Added `templates/core/PROJECT.yaml`, a fillable manifest template.

### Added — worked example

- `examples/bookmark-manager/`: ran `workflows/new-project.md` end-to-end against the § 123 canonical idea (`idea.md`, `PROJECT.yaml`, `NOTES.md`).

### Fixed

- `schemas/project.schema.yaml` and `templates/core/PROJECT.yaml` were missing `created_at`/`updated_at`, despite § 123 Step 2 and § 148 both requiring them. Found while building the worked example; added to the schema, template, and `workflows/new-project.md`'s capture/validate steps.
- § 123's own canonical classification used labels ("Search", "Data Platform", bare "AI", "Semantic Search") not in § 28's taxonomy. Added `ProjectFounder-idea.md` § 163.5 "Classification Escape Hatch" — a `types.other.<dimension>` free-text field alongside the enumerated `types.<dimension>` arrays — rather than extending § 28 on one project's evidence or dropping the information.

### Added

- Meta-research report on improving ProjectFounder, sourced from blogs, GitHub, Hacker News, and Reddit (`docs/research/2026-09-08-projectfounder-deep-research.md`).
- § 163 "v0.1.1 Amendments" in `ProjectFounder-idea.md`, turning the research report's P0 recommendations into called-out spec amendments:
  - § 163.1 Delta-spec / change-scoped artifact mode (amends § 21, § 90, § 108, § 122).
  - § 163.2 Explore-before-design step for non-`CREATE` project intents (amends § 27, § 123).
  - § 163.3 Human-readable plain-language tier for canonical artifacts (amends § 80, § 148).
  - § 163.4 Executable (vs. LLM-judged) validation for acceptance criteria (amends § 13, § 96, § 135).
- `docs/` directory as the home for this repo's own documentation (changelog, task backlog, meta-research), separate from the artifacts ProjectFounder generates for downstream projects.
- `docs/TASKS.md` — this repo's own build backlog, distinct from the `TASKS.md` artifact (spec § 91) ProjectFounder generates per downstream project.
- This repo's own instance of spec § 88 Core Project Artifacts, scoped to what has real content today (see `docs/DECISIONS.md` D004 for why the rest is deferred): `docs/DECISIONS.md`, `docs/ASSUMPTIONS.md`, `docs/CONSTRAINTS.md`, `docs/NON-GOALS.md`, `docs/OPEN-QUESTIONS.md`, `docs/LIMITATIONS.md`, `docs/REFERENCES.md`.

### Changed

- Moved `CHANGELOG.md` from the repo root to `docs/CHANGELOG.md`; `ProjectFounder-idea.md` § 145 (Repository Structure) updated to match.

## [0.1.0] - 2026-09-08

### Added

- Initial v0.1 repository scaffold matching `ProjectFounder-idea.md` § *Repository Structure*.
- Canonical specification (`ProjectFounder-idea.md`).
- `AGENT.md`, `AGENTS.md`, `CLAUDE.md` operational contracts.
- Draft agent contracts for the initial agent set (`agents/`).
- Draft skill contracts for the initial skill set (`skills/`).
- Draft policy configuration stubs (`config/`).
- Draft artifact schemas (`schemas/`).
- Directory scaffolding for `workflows/`, `resources/`, `templates/`, `checks/`, `commands/`, `examples/`, `output/`.
- Project README and branding icon.
