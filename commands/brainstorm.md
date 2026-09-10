# Command: brainstorm

> Entry point for running Discovery + Brainstorm against an already-classified project. Invoke this when a project has a `CLASSIFIED`, `CREATE`-intent `PROJECT.yaml` and is ready for its critical questions and initial feature candidates.

Status: Phase 1 (§ 140) — agent-executed, no code. This file is a thin trigger; the actual procedure lives in `workflows/brainstorm.md`.

## When to use

A project has already been founded and classified (`workflows/new-project.md` has run, `PROJECT.yaml.lifecycle == CLASSIFIED`, `intent == CREATE`), and the user wants to continue: surface critical unknowns and expand the idea into candidate features.

## What it does

Runs `workflows/brainstorm.md` via the `discovery-agent` and `brainstorm-agent` contracts (`agents/discovery-agent.md`, `agents/brainstorm-agent.md`):

1. Check preconditions (`lifecycle == CLASSIFIED`, `intent == CREATE`); stop if either fails.
2. Discover: derive and resolve critical questions into `ASSUMPTIONS.md`, `CONSTRAINTS.md`, and/or `OPEN-QUESTIONS.md`.
3. Brainstorm: expand the idea into a draft, uncategorized `FEATURES.md` candidate list.

Ends with the project at `lifecycle: DISCOVERY`. Does not run Research or any later-phase engine — those aren't implemented yet (see `docs/LIMITATIONS.md`).

## Inputs

- `PROJECT.yaml` at lifecycle `CLASSIFIED`, intent `CREATE` (required — from `workflows/new-project.md`).
- `idea.md` (required).

## Outputs

- `ASSUMPTIONS.md`
- `CONSTRAINTS.md`
- `OPEN-QUESTIONS.md`
- `FEATURES.md` (draft/uncategorized)

## See also

- `workflows/brainstorm.md` — the full procedure.
- `agents/discovery-agent.md`, `agents/brainstorm-agent.md` — the agent contracts this command drives.
- `commands/new-project.md` — must run first to produce a `CLASSIFIED` `PROJECT.yaml`.
