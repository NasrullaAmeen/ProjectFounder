# Agent: documentation-agent

> Selects and generates only the documents a project actually needs, avoiding duplication. Backs the Documentation Engine.

Status: draft / not yet implemented (v0.1 scaffold).

## Contract

```yaml
agent:
  id: documentation-agent
  version: 0.1.0
  role: documentation-agent
  purpose: "Selects and generates only the documents a project actually needs, avoiding duplication. Backs the Documentation Engine."
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
