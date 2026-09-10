# Command: requirements

> Entry point for running Gap Analysis + Feature Discovery + Requirements against a `DISCOVERY`-lifecycle project. Invoke this when a project has a draft `FEATURES.md` (from `commands/brainstorm.md`) and is ready to have its feature list gap-checked, tiered, and converted into requirements.

Status: Phase 1 (§ 140) — agent-executed, no code. This file is a thin trigger; the actual procedure lives in `workflows/requirements.md`.

## When to use

A project has already run Discovery + Brainstorm (`commands/brainstorm.md`, `PROJECT.yaml.lifecycle == DISCOVERY`, a draft `FEATURES.md` exists), and the user wants to continue: fill in anything Brainstorm missed, decide what's MVP versus later, and derive concrete requirements.

## What it does

Runs `workflows/requirements.md` via the `gap-analysis-agent`, `product-agent`, and `requirements-agent` contracts (`agents/gap-analysis-agent.md`, `agents/product-agent.md`, `agents/requirements-agent.md`):

1. Check preconditions (`lifecycle == DISCOVERY`, `FEATURES.md` exists); stop if either fails.
2. Gap Analysis: append any missed feature candidates to `FEATURES.md`.
3. Feature Discovery: tier every candidate into MVP/V1/V2/Future.
4. Requirements: write `REQUIREMENTS.md` for at least the MVP tier.

Ends with the project at `lifecycle: SCOPED`. Does not run Research or any later-phase engine — those aren't implemented yet (see `docs/LIMITATIONS.md`).

## Inputs

- `PROJECT.yaml` at lifecycle `DISCOVERY` (required — from `workflows/brainstorm.md`).
- `FEATURES.md`, `CONSTRAINTS.md`, `ASSUMPTIONS.md` (required — from `workflows/brainstorm.md`).

## Outputs

- `FEATURES.md` (gap-filled, fully tiered)
- `OPEN-QUESTIONS.md` (any genuine unknowns Gap Analysis found)
- `REQUIREMENTS.md`

## See also

- `workflows/requirements.md` — the full procedure.
- `agents/gap-analysis-agent.md`, `agents/product-agent.md`, `agents/requirements-agent.md` — the agent contracts this command drives.
- `commands/brainstorm.md` — must run first to produce a draft `FEATURES.md`.
