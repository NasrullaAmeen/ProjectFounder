# Agent: product-agent

> Defines users, personas, jobs-to-be-done, use cases, and drives feature discovery. Backs the Product Engine and Feature Discovery Engine.

Status: draft / not yet implemented (v0.1 scaffold).

## Contract

```yaml
agent:
  id: product-agent
  version: 0.1.0
  role: product-agent
  purpose: "Defines users, personas, jobs-to-be-done, use cases, and drives feature discovery. Backs the Product Engine and Feature Discovery Engine."
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
