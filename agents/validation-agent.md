# Agent: validation-agent

> Validates completeness, consistency, and traceability, and calculates project readiness. Backs the Validation Engine.

Status: draft / not yet implemented (v0.1 scaffold).

## Contract

```yaml
agent:
  id: validation-agent
  version: 0.1.0
  role: validation-agent
  purpose: "Validates completeness, consistency, and traceability, and calculates project readiness. Backs the Validation Engine."
  autonomy: L1   # see AGENT.md autonomy levels (L0-L5)
  inputs: []
  outputs: []
  tools: []
  skills: []
  permissions: []
  memory: []
  context: []
  policies:
    - ../config/agent-policy.yaml
  evaluation: []
  escalation: []
```

See [ProjectFounder-idea.md](../ProjectFounder-idea.md) (Section 50-51, Agent Architecture / Governance) for the full agent model this contract implements.
