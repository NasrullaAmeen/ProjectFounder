# AGENTS.md — Repository Conventions

Instructions for any coding agent (Claude Code, Codex, Cursor, Copilot, …) working **inside this repository** — i.e. implementing ProjectFounder itself, not running ProjectFounder against a downstream project.

## What this repo is

This repo *is* ProjectFounder: the system described in [`ProjectFounder-idea.md`](./ProjectFounder-idea.md). It currently ships as a **v0.1 scaffold** — directory structure, agent/skill/schema contracts, and config surface exist as drafts; engine logic and orchestration are not yet implemented.

## Repository conventions

- **The spec is canonical.** `ProjectFounder-idea.md` is the primary artifact. If code and spec disagree, either the code is wrong or the spec needs a deliberate, called-out update — never silently drift.
- **Contracts before implementation.** Every engine, agent, skill, workflow, and artifact has a documented contract (see §§ 146–152 of the spec, and the stub files under `agents/`, `skills/`, `schemas/`). Implement against the contract; update the contract if the implementation reveals it's wrong.
- **Engines vs. artifacts stay separate.** An engine is code/logic; an artifact is the persisted output. Don't merge the two into a single file/module.
- **Technology stays replaceable.** Don't hard-code a specific database, AI provider, or cloud vendor into core logic — route technology choices through the Resource model (`resources/`, `resource.schema.yaml`).
- **No speculative generation.** Don't scaffold every possible document/agent/workflow for every case — see spec § *What v0.1 Must NOT Do*. Build the smallest executable version of the architecture (§ *v0.1 Minimum Viable Definition*).
- **Follow the phase order.** New engine work should follow `ProjectFounder-idea.md` § *v0.1 Implementation Phases* (Foundation → Intelligence Core → Research → Architecture → AI/Agents → Budget/Business → Documentation → Validation → Implementation Planning) rather than jumping ahead.

## Coding expectations

- Keep new engines/skills/agents self-contained and testable independently (spec § 147, Engine Rules — item 10).
- Every engine must declare its inputs, outputs, and the artifacts it reads/writes before it's considered done (§ 146).
- Don't add error handling or fallbacks for scenarios the architecture doesn't yet support — validate at real boundaries only.
- Prefer extending an existing contract file over creating a parallel one that duplicates it.

## Validation

Before considering a change complete:

- Confirm any new/changed contract still matches its corresponding section of `ProjectFounder-idea.md`.
- If you add a new document type, artifact, or schema, register it in the relevant `config/*.yaml` and `schemas/*.schema.yaml` rather than leaving it implicit.
- Run whatever test suite exists for the touched area once implementation code exists (none yet, as of v0.1 scaffold).

## Forbidden behavior

- Do not silently overwrite a locked/human-approved artifact (spec § 106, Artifact Locking).
- Do not claim an engine or project is "production ready" without passing the Final Quality Gates (spec § 135).
- Do not commit secrets, API keys, or credentials to this repository.

## Agent handoff

See `AGENT.md` for the operational contract ProjectFounder follows when acting *as* the intelligence system, and `CLAUDE.md` for the Claude Code-specific adapter.
