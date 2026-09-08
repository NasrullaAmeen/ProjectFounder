# Workflow: new-project

> Founds a new project: captures the raw idea, classifies it, and creates its `PROJECT.yaml`. This is the Phase 0 slice of the full pipeline in `ProjectFounder-idea.md` § 1 (Executive Summary) and § 20 (Workflow Engine) — it stops at `CLASSIFIED`, since Discovery/Research/Architecture (Phase 1+) aren't implemented yet.

Status: Phase 0 (§ 140) — agent-executed, no code. A coding agent (e.g. via `commands/new-project.md`) follows the steps below directly; nothing here runs as a program.

## Contract

```yaml
workflow:
  id: new-project
  purpose: "Found a new project up through classification: idea.md -> PROJECT.yaml at lifecycle CLASSIFIED."
  trigger: commands/new-project.md, or a user directly asking to start/found a new project
  inputs:
    - idea.md   # or an inline idea description if idea.md doesn't exist yet
  steps:
    - id: capture
      does: "Write or confirm idea.md; create PROJECT.yaml from templates/core/PROJECT.yaml with a generated id/name; set created_at; set lifecycle: CAPTURED."
    - id: classify
      does: "Read config/project-types.yaml; assign one or more values per dimension (product/application/technical/ai/deployment) to PROJECT.yaml types, using types.other.<dimension> (§ 163.5) for labels not in the taxonomy; set intent (§ 27) and an initial complexity estimate (§ 116); set lifecycle: CLASSIFIED."
    - id: validate
      does: 'Check the filled PROJECT.yaml against schemas/project.schema.yaml by hand (no validator exists yet — § 163.4 "judged", not "executable").'
  engines: [project-engine]        # § 7.1 — no other engine's inputs are needed for this slice
  agents: [project-architect]
  skills: []                       # no dedicated skill exists (§ 142); the agent does this directly
  artifacts:
    - PROJECT.yaml
  approvals:
    - gate: classification ambiguous or intent is not CREATE
      requires: human confirmation before continuing (see agents/project-architect.md escalation rules)
  validation:
    - PROJECT.yaml conforms to schemas/project.schema.yaml
    - every value under `types.<dimension>` (not `types.other.<dimension>`) exists in config/project-types.yaml
    - lifecycle value exists in config/lifecycle.yaml states, reached via an allowed transition from the previous state
    - created_at and updated_at are both set (§ 148)
  failure_recovery:
    - condition: idea is too vague to classify
      action: record open questions in the project's own OPEN-QUESTIONS.md (§ 111) rather than guessing a classification
  outputs:
    - PROJECT.yaml at lifecycle CLASSIFIED, readiness R0, intent set, at least one classification per applicable dimension
```

## Steps in detail

### 1. Capture

1. If `idea.md` doesn't exist for this project yet, write it from what the user described.
2. Copy `templates/core/PROJECT.yaml` to the project's root as `PROJECT.yaml`.
3. Fill `id` (kebab-case slug) and `name`.
4. Set `created_at` to today's date; set `updated_at` to the same value (§ 148 requires both on every artifact). Leave `default_autonomy` at the template's `L1` default unless the user says otherwise (§ 163.10).
5. Set `lifecycle: CAPTURED` (already the template default) — this is the first transition per `config/lifecycle.yaml` (`IDEA -> CAPTURED`).

### 2. Classify

1. Read `config/project-types.yaml`. For each dimension (`product`, `application`, `technical`, `ai`, `deployment`), decide which listed values apply — zero, one, or several are valid (§ 28: "multiple classifications may apply"). If the idea genuinely needs a label that isn't in the taxonomy, put it under `types.other.<dimension>` (§ 163.5) — don't invent a new enumerated value and don't drop the information.
2. Set `intent` (§ 27). Default is `CREATE`; change it if the user's own words indicate otherwise (e.g. "clone", "rebuild", "improve an existing project").
3. If `intent` is not `CREATE`, do **not** proceed to Discovery once this workflow ends — the § 163.2 Explore step runs first, targeting lifecycle `EXPLORING` (§ 163.12). This workflow doesn't set that state itself (Explore isn't implemented, Phase 1/2) — leave the project at `CLASSIFIED` and tell the user the next stage is Explore, not Discovery.
4. Set an initial `complexity` estimate (§ 116) — a first guess, refined later by the Gap Analysis / Architecture engines (not yet implemented).
5. Advance `lifecycle: CLASSIFIED` (`CAPTURED -> CLASSIFIED` per `config/lifecycle.yaml`) and bump `updated_at`.

### 3. Validate

1. Re-read the filled `PROJECT.yaml` against `schemas/project.schema.yaml`: every required field present, every enum value valid, every `types` value present in `config/project-types.yaml`.
2. If anything doesn't check out, fix it before treating the workflow as complete — don't hand off a `PROJECT.yaml` that doesn't match its own schema.

## What happens next (not yet implemented)

For a `CREATE`-intent project, Discovery (Phase 1, § 297) is next; for any other intent, Explore (§ 163.2, targeting lifecycle `EXPLORING`) runs first. Neither has an engine, agent, or skill contract fleshed out yet. Stop here and tell the user which one is next and that it isn't implemented; don't fabricate either step to seem more complete than the repo actually is (§ 139 "hide uncertainty" is forbidden).
