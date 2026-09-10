# Agent: brainstorm-agent

> Expands the original idea into possibilities, feature candidates, variants, and alternative approaches. Backs the Brainstorm Engine.

Status: Phase 1 (§ 140) — agent-executed, no code (see `docs/DECISIONS.md` D005). Runs as the `brainstorm` step of `workflows/brainstorm.md`, after `discovery-agent`'s `discover` step.

## Contract

```yaml
agent:
  id: brainstorm-agent
  version: 0.1.0
  role: brainstorm-agent
  purpose: "Expands the original idea into possibilities, feature candidates, variants, and alternative approaches. Backs the Brainstorm Engine (§ 7.3)."
  autonomy: L1   # see AGENT.md autonomy levels (L0-L5)
  inputs:
    - idea.md
    - PROJECT.yaml
    - ASSUMPTIONS.md
    - CONSTRAINTS.md
  outputs:
    - FEATURES.md   # draft/uncategorized tier only — see docs/DECISIONS.md D011
  tools: []                  # agent-only Phase 1: uses the host agent's native file read/write, no custom tool defined yet
  skills: [brainstorm]
  permissions:
    - read: [idea.md, PROJECT.yaml, ASSUMPTIONS.md, CONSTRAINTS.md]
    - write: [FEATURES.md]
  memory: []
  context:
    - ../ProjectFounder-idea.md
  policies:
    - ../config/agent-policy.yaml
  evaluation: []
  escalation:
    - condition: a candidate idea directly contradicts a recorded CONSTRAINTS.md entry
      action: drop the candidate and note why in FEATURES.md rather than listing something infeasible as if it were a real option
    - condition: PROJECT.yaml.intent is not CREATE
      action: do not run — this agent assumes a greenfield idea; a non-CREATE project needs the § 163.2 Explore step first (not yet implemented, Phase 1/2)
```

See [ProjectFounder-idea.md](../ProjectFounder-idea.md) (Section 7.3, Brainstorm Engine; Section 50-51, Agent Architecture / Governance) for the full model this contract implements, and `workflows/brainstorm.md` for the concrete procedure this agent's `brainstorm` step follows. Categorizing `FEATURES.md` into MVP/V1/V2/Future tiers (§ 123 Step 9) is the Feature Discovery Engine's job (§ 7.7, `agents/product-agent.md`), not this agent's — not yet implemented.
