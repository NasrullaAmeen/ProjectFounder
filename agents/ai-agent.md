# Agent: ai-agent

> Determines where AI belongs in the project, whether agents/MCP are justified, and designs AI/agent/MCP architecture. Backs the AI, Agent, and MCP Engines.

Status: draft / not yet implemented (v0.1 scaffold).

## Contract

```yaml
agent:
  id: ai-agent
  version: 0.1.0
  role: ai-agent
  purpose: "Determines where AI belongs in the project, whether agents/MCP are justified, and designs AI/agent/MCP architecture. Backs the AI, Agent, and MCP Engines."
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
