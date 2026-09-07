# Command: new-project

> Entry point for founding a new project. Invoke this when a user gives ProjectFounder a raw idea and wants to start.

Status: Phase 0 (§ 140) — agent-executed, no code. This file is a thin trigger; the actual procedure lives in `workflows/new-project.md`.

## When to use

The user describes a project idea and wants ProjectFounder to start working on it — e.g. "I want to build a bookmark app like Raindrop" (the README's own example, and the § 123 worked journey).

## What it does

Runs `workflows/new-project.md` via the `project-architect` agent contract (`agents/project-architect.md`):

1. Capture the idea into `idea.md` and an initial `PROJECT.yaml` (from `templates/core/PROJECT.yaml`).
2. Classify it against `config/project-types.yaml`, set `intent` (§ 27) and an initial `complexity` estimate.
3. Check the result against `schemas/project.schema.yaml`.

Ends with the project at `lifecycle: CLASSIFIED`, `readiness: R0`. Does not run Discovery, Research, or any later-phase engine — those aren't implemented yet (see `docs/LIMITATIONS.md`).

## Inputs

- The user's description of the idea (required).
- An existing `idea.md`, if one already exists for this project (optional — skip re-capturing it).

## Outputs

- `idea.md`
- `PROJECT.yaml`

## See also

- `workflows/new-project.md` — the full procedure.
- `agents/project-architect.md` — the agent contract this command drives.
- `docs/OPEN-QUESTIONS.md` — Q1 (implementation stack) and Q8 (lifecycle loop-backs) are relevant open questions this command's output may surface.
