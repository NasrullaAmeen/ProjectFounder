# Agent: project-architect

> Owns project identity, classification, lifecycle, and orchestrates handoffs between all other agents. Backs the Project Engine and Workflow Engine.

Status: Phase 0 (§ 140) — the founding responsibility (identity, classification, initial lifecycle state) is implemented as an agent-executed workflow (`workflows/new-project.md`, invoked via `commands/new-project.md`); no code/runtime exists, so "implemented" here means a coding agent follows this contract directly, not that a program executes it. Orchestrating handoffs to other agents (Phase 1+) is not yet implemented.

## Contract

```yaml
agent:
  id: project-architect
  version: 0.1.0
  role: project-architect
  purpose: "Owns project identity, classification, lifecycle, and orchestrates handoffs between all other agents. Backs the Project Engine and Workflow Engine."
  autonomy: L1   # see AGENT.md autonomy levels (L0-L5) — proposes, human approves before lifecycle/readiness advance past CLASSIFIED
  inputs:
    - idea.md               # the raw idea being founded (§ 88)
    - schemas/project.schema.yaml
    - config/project-types.yaml
    - config/lifecycle.yaml
  outputs:
    - PROJECT.yaml           # § 120 Project Manifest
  tools: []                  # agent-only Phase 0: uses the host agent's native file read/write, no custom tool defined yet
  skills: []                 # no dedicated skill exists for project founding (§ 142 doesn't list one) — this agent does it directly
  permissions:
    - read: [idea.md, schemas/project.schema.yaml, config/project-types.yaml, config/lifecycle.yaml]
    - write: [PROJECT.yaml]
  memory: []
  context:
    - ../ProjectFounder-idea.md
  policies:
    - ../config/agent-policy.yaml
    - ../config/project-types.yaml
    - ../config/lifecycle.yaml
  evaluation: []
  escalation:
    - condition: classification is ambiguous across two or more values in the same dimension
      action: record all plausible values in PROJECT.yaml types, do not guess a single one
    - condition: intent is not CREATE
      action: do not proceed to Discovery — hand off to the § 163.2 Explore step first
    - condition: intent is ambiguous across two or more of § 27's values
      action: >
        pick the single closest-fit value for `intent` (it stays single-valued;
        this is not the § 163.5 `other` pattern, which only applies to `types`),
        but record every rejected candidate and the reasoning in the project's
        OPEN-QUESTIONS.md (§ 111) instead of silently resolving it (§ 163.13)
```

See [ProjectFounder-idea.md](../ProjectFounder-idea.md) (Section 50-51, Agent Architecture / Governance) for the full agent model this contract implements, and `workflows/new-project.md` for the concrete Phase 0 procedure this agent follows.
