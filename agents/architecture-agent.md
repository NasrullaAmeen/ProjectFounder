# Agent: architecture-agent

> Designs system, data, API, and UX architecture from validated requirements. Backs the Architecture, Data, API, and UX/UI Engines.

Status: draft / not yet implemented (v0.1 scaffold).

## Contract

```yaml
agent:
  id: architecture-agent
  version: 0.1.0
  role: architecture-agent
  purpose: "Designs system, data, API, and UX architecture from validated requirements. Backs the Architecture, Data, API, and UX/UI Engines."
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
  escalation:
    - condition: REQUIREMENTS.md doesn't exist yet
      action: do not run — Architecture designs from validated requirements (§ 163.15); this holds whether the project reached RESEARCHING via SCOPED or directly from DISCOVERY, so run Gap Analysis/Feature Discovery/Requirements first regardless of path
```

See [ProjectFounder-idea.md](../ProjectFounder-idea.md) (Section 50-51, Agent Architecture / Governance) for the full agent model this contract implements.
