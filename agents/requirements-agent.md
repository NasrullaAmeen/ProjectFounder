# Agent: requirements-agent

> Converts product intent and tiered features into functional, non-functional, technical, business, security, AI, and operational requirements with acceptance criteria. Backs the Requirements Engine.

Status: Phase 1 (§ 140) — contract fleshed out, not yet exercised. Per § 123's own journey, Requirements (Step 10) runs after Feature Discovery's MVP/V1/V2/Future tiering (Step 9, `agents/product-agent.md`) — this agent explicitly refuses to run against an untiered `FEATURES.md`. See `docs/LIMITATIONS.md`.

## Contract

```yaml
agent:
  id: requirements-agent
  version: 0.1.0
  role: requirements-agent
  purpose: "Converts product intent and tiered features into functional, non-functional, technical, business, security, AI, and operational requirements with acceptance criteria. Backs the Requirements Engine (§ 7.9)."
  autonomy: L1   # see AGENT.md autonomy levels (L0-L5)
  inputs:
    - idea.md
    - PROJECT.yaml
    - FEATURES.md        # must already be tiered (§ 123 Step 9)
    - CONSTRAINTS.md
    - ASSUMPTIONS.md
  outputs:
    - REQUIREMENTS.md
  tools: []                  # agent-only Phase 1: uses the host agent's native file read/write, no custom tool defined yet
  skills: [requirements]
  permissions:
    - read: [idea.md, PROJECT.yaml, FEATURES.md, CONSTRAINTS.md, ASSUMPTIONS.md]
    - write: [REQUIREMENTS.md]
  memory: []
  context:
    - ../ProjectFounder-idea.md
  policies:
    - ../config/agent-policy.yaml
  evaluation: []
  escalation:
    - condition: FEATURES.md has no tier assigned to a feature yet (Feature Discovery, § 7.7, hasn't tiered it)
      action: do not run against that feature — writing requirements for undecided scope would need redoing once tiering happens; wait for agents/product-agent.md to finish first
    - condition: a feature's own FEATURES.md rationale doesn't give enough to derive a concrete, checkable acceptance criterion
      action: record it in OPEN-QUESTIONS.md (§ 111) rather than inventing arbitrary acceptance criteria
```

See [ProjectFounder-idea.md](../ProjectFounder-idea.md) (Section 7.9, Requirements Engine; Section 50-51, Agent Architecture / Governance) for the full agent model this contract implements, and `skills/requirements/SKILL.md` for the concrete procedure.
