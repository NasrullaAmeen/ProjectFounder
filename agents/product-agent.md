# Agent: product-agent

> Defines users, personas, jobs-to-be-done, use cases, and drives feature discovery. Backs the Product Engine and Feature Discovery Engine.

Status: Phase 1 (§ 140) — only the Feature Discovery Engine (§ 7.7) half of this contract is fleshed out below, not yet exercised (no workflow wired to it yet — see `docs/LIMITATIONS.md`). The Product Engine (§ 7.6) half — personas, jobs-to-be-done, user research — stays a blank stub; it isn't in Phase 1's declared scope (`docs/TASKS.md` lists Discovery/Brainstorm/Classification/Requirements/Feature Discovery/Gap Analysis, not Product) and § 79 User Research needs live user access this repo doesn't have.

## Contract

```yaml
agent:
  id: product-agent
  version: 0.1.0
  role: product-agent
  purpose: "Defines users, personas, jobs-to-be-done, use cases, and drives feature discovery. Backs the Product Engine and Feature Discovery Engine."
  autonomy: L1   # see AGENT.md autonomy levels (L0-L5)
  inputs:
    - idea.md
    - PROJECT.yaml
    - FEATURES.md        # draft, from Brainstorm + Gap Analysis (§ 123 Steps 5, 8)
    - CONSTRAINTS.md
    - ASSUMPTIONS.md
  outputs:
    - FEATURES.md         # tiers candidates into MVP/V1/V2/Future in place (§ 123 Step 9)
  tools: []                  # agent-only Phase 1: uses the host agent's native file read/write, no custom tool defined yet
  skills: [feature-discovery]
  permissions:
    - read: [idea.md, PROJECT.yaml, FEATURES.md, CONSTRAINTS.md, ASSUMPTIONS.md]
    - write: [FEATURES.md]
  memory: []
  context:
    - ../ProjectFounder-idea.md
  policies:
    - ../config/agent-policy.yaml
  evaluation: []
  escalation:
    - condition: a candidate's tier depends on competitive positioning (§ 7.7 "competitive features") that needs market research
      action: tier it using only internal signals (fit with the idea, constraints, complexity) and mark it "tier: provisional — competitive dimension not assessed" rather than asserting unearned confidence; Research (§ 7.4, Phase 2) isn't built yet
    - condition: FEATURES.md doesn't exist yet, or Gap Analysis hasn't run on it
      action: do not run — Feature Discovery tiers Brainstorm's (and Gap Analysis's) draft list, it doesn't create one from scratch
```

See [ProjectFounder-idea.md](../ProjectFounder-idea.md) (Section 7.7, Feature Discovery Engine; Section 50-51, Agent Architecture / Governance) for the full agent model this contract implements, and `skills/feature-discovery/SKILL.md` for the concrete procedure.
