# Skill: feature-discovery

> Find obvious, implied, missing, and competitive features for the product.

Status: Phase 1 (§ 140) — contract fleshed out, not yet exercised (see `agents/product-agent.md` for why).

## Contract

```yaml
skill:
  id: feature-discovery
  version: 0.1.0
  purpose: "Find obvious, implied, missing, and competitive features for the product."
  inputs:
    - idea.md
    - PROJECT.yaml
    - FEATURES.md
    - CONSTRAINTS.md
    - ASSUMPTIONS.md
  procedure:
    - "Read every candidate already in FEATURES.md (from Brainstorm and Gap Analysis) — this skill tiers an existing list, it doesn't generate new candidates itself (that's Brainstorm's/Gap Analysis's job)."
    - "For each candidate, assign a tier: MVP (the idea fails at its core purpose without it), V1 (materially improves it but isn't load-bearing), V2 (a real improvement, not urgent), or Future (plausible, no near-term case for it) — § 123 Step 9."
    - "Ground each tier assignment in a one-clause reason tied to CONSTRAINTS.md/ASSUMPTIONS.md or the idea itself, the same rationale discipline Brainstorm already applies — no unexplained tier assignments."
    - "Where a tier assignment would depend on competitive positioning (is this feature table-stakes because every competitor has it?) and no research exists yet, tier using internal signals only and mark it provisional rather than asserting a confidence the engine doesn't have."
  tools: []
  outputs:
    - FEATURES.md   # tier added to each existing entry, in place
  validation:
    - "Every candidate in FEATURES.md has exactly one tier (MVP/V1/V2/Future) after this runs — none left untiered."
    - "Every tier assignment has a stated reason, not just a bare label."
    - "A provisional tier (competitive dimension unassessed) is marked as such, not presented with full confidence."
  failure_conditions:
    - "FEATURES.md doesn't exist yet, or Gap Analysis hasn't been run on it — escalate (per agents/product-agent.md) rather than tiering an incomplete or nonexistent list."
```

See [ProjectFounder-idea.md](../../ProjectFounder-idea.md) (Section 7.7, Feature Discovery Engine; Section 10, Skills Engine; § 123 Step 9) for the full skill model this contract implements.
