# Agent: discovery-agent

> Surfaces hidden requirements, missing information, unclear goals, assumptions, constraints, unknowns, open questions, and blockers by asking only critical discovery questions. Backs the Discovery Engine.

Status: Phase 1 (§ 140) — agent-executed, no code (same shape as `agents/project-architect.md`'s Phase 0 slice; see `docs/DECISIONS.md` D005, which applies until an engine needs deterministic logic an agent can't do by reading files). Runs as the `discover` step of `workflows/brainstorm.md`.

## Contract

```yaml
agent:
  id: discovery-agent
  version: 0.1.0
  role: discovery-agent
  purpose: "Surfaces hidden requirements, missing information, unclear goals, assumptions, constraints, unknowns, open questions, and blockers by asking only critical discovery questions. Backs the Discovery Engine (§ 7.2)."
  autonomy: L1   # see AGENT.md autonomy levels (L0-L5) — proposes assumptions/questions, human resolves genuinely blocking ones
  inputs:
    - idea.md
    - PROJECT.yaml
  outputs:
    - ASSUMPTIONS.md
    - CONSTRAINTS.md
    - OPEN-QUESTIONS.md
  tools: []                  # agent-only Phase 1: uses the host agent's native file read/write, no custom tool defined yet
  skills: [discovery]
  permissions:
    - read: [idea.md, PROJECT.yaml]
    - write: [ASSUMPTIONS.md, CONSTRAINTS.md, OPEN-QUESTIONS.md]
  memory: []
  context:
    - ../ProjectFounder-idea.md
  policies:
    - ../config/agent-policy.yaml
  evaluation: []
  escalation:
    - condition: a critical question has no reasonable default and no answer is available
      action: record it in OPEN-QUESTIONS.md (§ 111) rather than guessing or blocking the workflow
    - condition: PROJECT.yaml.intent is not CREATE
      action: do not run — this agent assumes a greenfield idea; a non-CREATE project needs the § 163.2 Explore step first (not yet implemented, Phase 1/2)
```

See [ProjectFounder-idea.md](../ProjectFounder-idea.md) (Section 7.2, Discovery Engine; Section 50-51, Agent Architecture / Governance) for the full model this contract implements, and `workflows/brainstorm.md` for the concrete procedure this agent's `discover` step follows.
