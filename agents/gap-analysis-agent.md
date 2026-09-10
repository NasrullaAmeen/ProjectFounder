# Agent: gap-analysis-agent

> Finds missing requirements, features, documentation, architecture, security controls, operational systems, testing, budget assumptions, AI safeguards, and deployment considerations. Backs the Gap Analysis Engine.

Status: Phase 1 (§ 140) — contract fleshed out, not yet exercised. Unlike `discovery-agent`/`brainstorm-agent`, this contract has no workflow wired to it yet: per § 123's own journey, Gap Analysis (Step 8) runs *between* Brainstorm (Step 5, done) and Feature Discovery's MVP/V1/V2/Future tiering (Step 9), and several of its categories (architecture, security, budget, operational) need artifacts (`ARCHITECTURE.md`, `BUDGET.md`, `TECH-STACK.md`) that don't exist until Phase 3/5. See `docs/LIMITATIONS.md`.

## Contract

```yaml
agent:
  id: gap-analysis-agent
  version: 0.1.0
  role: gap-analysis-agent
  purpose: "Finds missing requirements, features, documentation, architecture, security controls, operational systems, testing, budget assumptions, AI safeguards, and deployment considerations. Backs the Gap Analysis Engine (§ 7.8)."
  autonomy: L1   # see AGENT.md autonomy levels (L0-L5)
  inputs:
    - idea.md
    - PROJECT.yaml
    - FEATURES.md       # draft, from Brainstorm (§ 123 Step 5) — Gap Analysis runs before Feature Discovery's tiering (Step 9)
    - CONSTRAINTS.md
    - ASSUMPTIONS.md
    - OPEN-QUESTIONS.md
  outputs:
    - FEATURES.md        # appends newly-found candidates, same draft/uncategorized tier as Brainstorm's — see docs/DECISIONS.md D012
    - OPEN-QUESTIONS.md   # only for a found gap that's genuinely undecided, not a straightforward missing feature
  tools: []                  # agent-only Phase 1: uses the host agent's native file read/write, no custom tool defined yet
  skills: [gap-analysis]
  permissions:
    - read: [idea.md, PROJECT.yaml, FEATURES.md, CONSTRAINTS.md, ASSUMPTIONS.md, OPEN-QUESTIONS.md]
    - write: [FEATURES.md, OPEN-QUESTIONS.md]
  memory: []
  context:
    - ../ProjectFounder-idea.md
  policies:
    - ../config/agent-policy.yaml
  evaluation: []
  escalation:
    - condition: a gap category needs an artifact that doesn't exist yet (ARCHITECTURE.md, BUDGET.md, TECH-STACK.md — Phase 3/5)
      action: skip that category explicitly and say so, rather than fabricating findings against an artifact that isn't there
    - condition: a found gap is a genuine unknown, not a straightforward missing feature (e.g. "should deleted bookmarks be recoverable, and for how long?")
      action: record it in OPEN-QUESTIONS.md (§ 111) instead of FEATURES.md
    - condition: FEATURES.md doesn't exist yet (Brainstorm hasn't run)
      action: do not run — Gap Analysis checks Brainstorm's draft list for what it missed, it doesn't create one from scratch
```

See [ProjectFounder-idea.md](../ProjectFounder-idea.md) (Section 7.8, Gap Analysis Engine; Section 50-51, Agent Architecture / Governance) for the full model this contract implements, and `skills/gap-analysis/SKILL.md` for the concrete procedure.
