# Agent: technology-agent

> Discovers and evaluates replaceable technology resources (languages, frameworks, databases, AI providers, hosting). Backs the Resource Engine.

Status: draft / not yet implemented (v0.1 scaffold).

## Contract

```yaml
agent:
  id: technology-agent
  version: 0.1.0
  role: technology-agent
  purpose: "Discovers and evaluates replaceable technology resources (languages, frameworks, databases, AI providers, hosting). Backs the Resource Engine."
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
