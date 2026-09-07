# Agent: research-agent

> Researches competitors, GitHub repositories, technologies, APIs, and market context, recording evidence with sources. Backs the Research Engine.

Status: draft / not yet implemented (v0.1 scaffold).

## Contract

```yaml
agent:
  id: research-agent
  version: 0.1.0
  role: research-agent
  purpose: "Researches competitors, GitHub repositories, technologies, APIs, and market context, recording evidence with sources. Backs the Research Engine."
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
