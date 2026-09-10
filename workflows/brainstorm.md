# Workflow: brainstorm

> Runs Discovery then Brainstorm against an already-`CLASSIFIED`, `CREATE`-intent project: `idea.md` + `PROJECT.yaml` → `ASSUMPTIONS.md` / `CONSTRAINTS.md` / `OPEN-QUESTIONS.md` / `FEATURES.md` (draft tier), lifecycle → `DISCOVERY`. This is the Phase 1 slice of the pipeline (§ 123 Steps 4–5) — named `brainstorm` per § 143's "Initial Workflows" list, which names `brainstorm` but not a separate `discovery` workflow; the two engines run as one invokable action, the same way `new-project` already bundles capture+classify+validate.

Status: Phase 1 (§ 140) — agent-executed, no code (see `docs/DECISIONS.md` D005). A coding agent (e.g. via `commands/brainstorm.md`) follows the steps below directly; nothing here runs as a program.

## Contract

```yaml
workflow:
  id: brainstorm
  purpose: "Run Discovery then Brainstorm against a CLASSIFIED, CREATE-intent project: idea.md + PROJECT.yaml -> ASSUMPTIONS.md/CONSTRAINTS.md/OPEN-QUESTIONS.md/FEATURES.md, lifecycle -> DISCOVERY."
  trigger: commands/brainstorm.md, or a user asking to continue discovery/brainstorming on an already-classified project
  preconditions:                # § 163.8 Actions, Not Phases
    - "PROJECT.yaml.lifecycle == CLASSIFIED"
    - "PROJECT.yaml.intent == CREATE"
  inputs:
    - PROJECT.yaml
    - idea.md
  steps:
    - id: precondition-check
      does: "Confirm both preconditions above. If intent != CREATE, stop and tell the user the § 163.2 Explore step must run first (not yet implemented, Phase 1/2) — do not run Discovery against a non-greenfield idea. If lifecycle != CLASSIFIED, stop and point to workflows/new-project.md."
    - id: discover
      does: "Run agents/discovery-agent.md via skills/discovery/: derive and resolve critical questions into ASSUMPTIONS.md, CONSTRAINTS.md, and/or OPEN-QUESTIONS.md entries."
    - id: brainstorm
      does: "Run agents/brainstorm-agent.md via skills/brainstorm/: expand the idea into a draft, uncategorized FEATURES.md candidate list, consistent with the constraints/assumptions the discover step just recorded."
    - id: advance-lifecycle
      does: "Set lifecycle: DISCOVERY (CLASSIFIED -> DISCOVERY per config/lifecycle.yaml) and bump updated_at."
  engines: [discovery-engine, brainstorm-engine]   # § 7.2, § 7.3
  agents: [discovery-agent, brainstorm-agent]
  skills: [discovery, brainstorm]
  artifacts:
    - ASSUMPTIONS.md
    - CONSTRAINTS.md
    - OPEN-QUESTIONS.md
    - FEATURES.md
  approvals:
    - gate: any critical discovery question resolves to a genuinely blocking OPEN-QUESTIONS.md entry
      requires: human confirmation before treating discovery as sufficient to proceed further (Research, Phase 2, isn't implemented yet regardless)
  validation:
    - PROJECT.yaml.lifecycle == DISCOVERY afterward
    - every critical question the discover step asked has exactly one resolution (inline answer, ASSUMPTIONS.md, CONSTRAINTS.md, or OPEN-QUESTIONS.md entry)
    - FEATURES.md exists and is explicitly marked draft/uncategorized, so it isn't mistaken for the Feature Discovery Engine's finished, tiered output
  failure_recovery:
    - condition: PROJECT.yaml isn't at lifecycle CLASSIFIED or intent isn't CREATE when this workflow starts
      action: stop before writing anything; tell the user which precondition failed and what to run instead (workflows/new-project.md, or wait for the Explore step)
  outputs:
    - PROJECT.yaml at lifecycle DISCOVERY
    - ASSUMPTIONS.md, CONSTRAINTS.md, OPEN-QUESTIONS.md, FEATURES.md populated for the project
```

## Steps in detail

### 1. Precondition check

Read `PROJECT.yaml`. If `intent` isn't `CREATE`, stop — this workflow assumes a greenfield idea; a non-`CREATE` project needs the § 163.2 Explore step first, and Explore has no workflow yet (Phase 1/2). If `lifecycle` isn't `CLASSIFIED`, stop and point the user at `workflows/new-project.md` instead.

### 2. Discover

Follow `skills/discovery/SKILL.md`'s procedure: derive a small set of critical questions from the idea and its classification (§ 123 Step 4 style — primary users, mandatory vs. optional requirements, anything genuinely ambiguous), and resolve each one as an inline answer, an `ASSUMPTIONS.md` entry, a `CONSTRAINTS.md` entry, or an `OPEN-QUESTIONS.md` entry. Create these three files for the project if they don't exist yet (they're part of § 88's Core Project Artifacts, scoped in per D004's "only what has real content today" rule — Discovery is what gives them real content for a downstream project, unlike the worked examples in `examples/`, which only got `PROJECT.yaml` at Phase 0).

### 3. Brainstorm

Follow `skills/brainstorm/SKILL.md`'s procedure: read the `ASSUMPTIONS.md`/`CONSTRAINTS.md` just written, and expand the idea into a draft `FEATURES.md` candidate list — plain names with one-clause rationales, explicitly *not* categorized into MVP/V1/V2/Future (that's the Feature Discovery Engine, § 7.7, a later Phase 1 slice — see `docs/DECISIONS.md` D011 for why `FEATURES.md` is reused here rather than a separate draft-only file).

### 4. Advance lifecycle

Set `lifecycle: DISCOVERY` and bump `updated_at`. This workflow doesn't advance further — Research (§ 123 Step 6, Phase 2) is next but not implemented yet; stop here and tell the user that, per `AGENTS.md`'s "no speculative generation" and § 139's "don't hide uncertainty."

## What happens next (not yet implemented)

Research (Phase 2, § 7.4) and Resource Discovery (Phase 2, § 7.5) come next in the § 123 journey (Steps 6–7), followed by Gap Analysis, Feature Discovery's MVP/V1/V2/Future tiering, and Requirements (Steps 8–10, the rest of Phase 1). None of those have an engine, agent, or skill contract fleshed out yet. Don't fabricate any of them to seem more complete than the repo actually is.
