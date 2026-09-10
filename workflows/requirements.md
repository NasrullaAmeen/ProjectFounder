# Workflow: requirements

> Runs Gap Analysis, then Feature Discovery, then Requirements against a `DISCOVERY`-lifecycle project with a draft `FEATURES.md`: `FEATURES.md` (draft) → `FEATURES.md` (gap-filled + tiered) → `REQUIREMENTS.md`, lifecycle → `SCOPED`. This is the rest of Phase 1's pipeline (§ 123 Steps 8–10) — named `requirements` after its terminal artifact, the same convention `brainstorm` used. Runs independently of Research (Phase 2) per § 163.8 Actions, Not Phases — its own preconditions don't require Research, though the competitive-positioning sub-case of Feature Discovery degrades to "provisional" without it.

Status: Phase 1 (§ 140) — agent-executed, no code (see `docs/DECISIONS.md` D005). A coding agent (e.g. via `commands/requirements.md`) follows the steps below directly; nothing here runs as a program.

## Contract

```yaml
workflow:
  id: requirements
  purpose: "Run Gap Analysis, Feature Discovery, then Requirements against a DISCOVERY-lifecycle project: FEATURES.md (draft) -> FEATURES.md (gap-filled + tiered) -> REQUIREMENTS.md, lifecycle -> SCOPED."
  trigger: commands/requirements.md, or a user asking to scope/tier features and derive requirements for an already-brainstormed project
  preconditions:                # § 163.8 Actions, Not Phases
    - "PROJECT.yaml.lifecycle == DISCOVERY"
    - "FEATURES.md exists and is still draft/uncategorized (workflows/brainstorm.md has run)"
  inputs:
    - PROJECT.yaml
    - idea.md
    - FEATURES.md
    - CONSTRAINTS.md
    - ASSUMPTIONS.md
    - OPEN-QUESTIONS.md
  steps:
    - id: precondition-check
      does: "Confirm both preconditions above. If FEATURES.md doesn't exist, stop and point to workflows/brainstorm.md. If lifecycle != DISCOVERY, stop and say which workflow reaches DISCOVERY (workflows/brainstorm.md) or explain this project has already moved past it."
    - id: gap-analysis
      does: "Run agents/gap-analysis-agent.md via skills/gap-analysis/: append any missed feature candidates to FEATURES.md (still draft/uncategorized, same rationale discipline as Brainstorm's own entries), route genuine unknowns to OPEN-QUESTIONS.md instead. Explicitly skip categories with no artifact yet (architecture, security, budget, deployment — Phase 3/5) and say so."
    - id: feature-discovery
      does: "Run agents/product-agent.md via skills/feature-discovery/: tier every FEATURES.md candidate, including Gap Analysis's additions, into MVP/V1/V2/Future in place. Mark any tier that depended on unavailable competitive research as provisional."
    - id: requirements
      does: "Run agents/requirements-agent.md via skills/requirements/: write REQUIREMENTS.md starting with MVP-tier features, each requirement traced back to its FEATURES.md entry, with acceptance criteria classified executable/judged per § 163.4."
    - id: advance-lifecycle
      does: "Set lifecycle: SCOPED (DISCOVERY -> SCOPED per config/lifecycle.yaml, § 163.14) and bump updated_at."
  engines: [gap-analysis-engine, feature-discovery-engine, requirements-engine]   # § 7.8, § 7.7, § 7.9
  agents: [gap-analysis-agent, product-agent, requirements-agent]
  skills: [gap-analysis, feature-discovery, requirements]
  artifacts:
    - FEATURES.md
    - OPEN-QUESTIONS.md
    - REQUIREMENTS.md
  approvals:
    - gap: any MVP-tier feature ends up with only judged (not executable) acceptance criteria
      requires: nothing blocking yet — § 163.4 only requires the ratio be reported, not that every criterion be executable this early
  validation:
    - PROJECT.yaml.lifecycle == SCOPED afterward
    - every FEATURES.md candidate has exactly one tier (MVP/V1/V2/Future) after the feature-discovery step
    - every MVP-tier feature has at least one REQUIREMENTS.md entry, each with an ID, a type tag, and classified acceptance criteria
    - no REQUIREMENTS.md entry exists without a traceable FEATURES.md source
  failure_recovery:
    - condition: PROJECT.yaml isn't at lifecycle DISCOVERY, or FEATURES.md doesn't exist, when this workflow starts
      action: stop before writing anything; tell the user which precondition failed and what to run instead (workflows/brainstorm.md)
  outputs:
    - PROJECT.yaml at lifecycle SCOPED
    - FEATURES.md gap-filled and fully tiered
    - REQUIREMENTS.md populated for at least the MVP tier
```

## Steps in detail

### 1. Precondition check

Read `PROJECT.yaml` and check for `FEATURES.md`. If `FEATURES.md` doesn't exist, stop — `workflows/brainstorm.md` hasn't run yet. If `lifecycle` isn't `DISCOVERY`, stop and say so (either it needs `workflows/brainstorm.md` first, or it's already past this point).

### 2. Gap Analysis

Follow `skills/gap-analysis/SKILL.md`'s procedure: check `FEATURES.md`'s draft list against obvious missing concerns (account/data lifecycle, privacy, abuse/rate-limiting, import/export completeness) and append any real gaps found, in the same draft/uncategorized style Brainstorm already uses. Explicitly skip categories with no owning artifact yet — don't fabricate findings against `ARCHITECTURE.md`/`BUDGET.md`, which don't exist (Phase 3/5).

### 3. Feature Discovery

Follow `skills/feature-discovery/SKILL.md`'s procedure: tier every candidate now in `FEATURES.md` (Brainstorm's original entries plus Gap Analysis's additions) into MVP/V1/V2/Future, each with a stated reason. Where a tier call would need competitive research that doesn't exist yet (Phase 2), tier from internal signals only and mark it provisional rather than asserting unearned confidence.

### 4. Requirements

Follow `skills/requirements/SKILL.md`'s procedure: write `REQUIREMENTS.md`, starting with the MVP tier — one or more `REQ-<NNN>` entries per feature, each a SHALL/SHOULD statement tagged by type (functional/non-functional/technical/business/security/AI/operational), with acceptance criteria written as GIVEN/WHEN/THEN wherever mechanically checkable and classified executable/judged (§ 163.4).

### 5. Advance lifecycle

Set `lifecycle: SCOPED` and bump `updated_at` (§ 163.14 — this doesn't mean Research happened, only that Gap Analysis/Feature Discovery/Requirements did).

## What happens next (not yet implemented)

Research (Phase 2, § 7.4) and Resource Discovery (Phase 2, § 7.5) still haven't run for a project that took this branch — `SCOPED`'s only legal next state is `RESEARCHING` (`config/lifecycle.yaml`), and neither has an engine, agent, or skill contract yet. Whether Architecture (`DESIGNING`) should require this workflow's `REQUIREMENTS.md` even when a project reaches `RESEARCHING` by the other branch (straight from `DISCOVERY`) is an open question — see `docs/OPEN-QUESTIONS.md` Q10. Don't fabricate either to seem more complete than the repo actually is.
