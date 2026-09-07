# Changelog

All notable changes to this project will be documented in this file.

This changelog tracks ProjectFounder's own development (the repo you're reading), not the artifacts ProjectFounder generates for downstream projects — those get their own `output/<project>/` history.

## [Unreleased]

### Added

- Meta-research report on improving ProjectFounder, sourced from blogs, GitHub, Hacker News, and Reddit (`docs/research/2026-09-08-projectfounder-deep-research.md`).
- § 163 "v0.1.1 Amendments" in `ProjectFounder-idea.md`, turning the research report's P0 recommendations into called-out spec amendments:
  - § 163.1 Delta-spec / change-scoped artifact mode (amends § 21, § 90, § 108, § 122).
  - § 163.2 Explore-before-design step for non-`CREATE` project intents (amends § 27, § 123).
  - § 163.3 Human-readable plain-language tier for canonical artifacts (amends § 80, § 148).
  - § 163.4 Executable (vs. LLM-judged) validation for acceptance criteria (amends § 13, § 96, § 135).
- `docs/` directory as the home for this repo's own documentation (changelog, task backlog, meta-research), separate from the artifacts ProjectFounder generates for downstream projects.
- `docs/TASKS.md` — this repo's own build backlog, distinct from the `TASKS.md` artifact (spec § 91) ProjectFounder generates per downstream project.

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
