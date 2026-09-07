# Agent: project-architect

> Owns project identity, classification, lifecycle, and orchestrates handoffs between all other agents. Backs the Project Engine and Workflow Engine.

Status: draft / not yet implemented (v0.1 scaffold).

## Contract

```yaml
agent:
  id: project-architect
  version: 0.1.0
  role: project-architect
  purpose: "Owns project identity, classification, lifecycle, and orchestrates handoffs between all other agents. Backs the Project Engine and Workflow Engine."
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
