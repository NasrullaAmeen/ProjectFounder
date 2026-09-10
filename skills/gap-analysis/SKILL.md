# Skill: gap-analysis

> Find missing requirements, features, documentation, and operational concerns.

Status: Phase 1 (§ 140) — contract fleshed out, not yet exercised (see `agents/gap-analysis-agent.md` for why: no workflow wired to it yet, and several categories need artifacts that don't exist until Phase 3/5).

## Contract

```yaml
skill:
  id: gap-analysis
  version: 0.1.0
  purpose: "Find missing requirements, features, documentation, and operational concerns."
  inputs:
    - idea.md
    - PROJECT.yaml
    - FEATURES.md
    - CONSTRAINTS.md
    - ASSUMPTIONS.md
  procedure:
    - "Read FEATURES.md's draft candidate list plus CONSTRAINTS.md/ASSUMPTIONS.md — gap-check against what's already there, don't re-derive from idea.md alone (that's Brainstorm's job, already done)."
    - "Check each § 7.8 category that has a real artifact to check against today: features (compare against categories a similar project would obviously need — account/data lifecycle, privacy, abuse/rate-limiting, import/export completeness — and flag any FEATURES.md is missing) and requirements-adjacent concerns (anything a feature implies but doesn't state, e.g. a 'search' feature implying an indexing/freshness concern)."
    - "Explicitly skip categories with no artifact yet (documentation beyond what § 88 already covers, architecture, security controls, budget assumptions, deployment considerations) — note them as skipped, not silently ignored, per agents/gap-analysis-agent.md's escalation rule."
    - "For each found feature-shaped gap, append it to FEATURES.md in the same draft/uncategorized style as Brainstorm's own entries, with a rationale tying it to a concrete risk (e.g. 'Account deletion — without it, the free/self-hosted constraint has no data-lifecycle story')."
    - "For a found gap that's a genuine unknown rather than an obvious missing feature, record it in OPEN-QUESTIONS.md instead."
  tools: []
  outputs:
    - FEATURES.md         # appended, not replaced
    - OPEN-QUESTIONS.md   # only for genuine unknowns found
  validation:
    - "Every appended FEATURES.md candidate has a rationale, same as Brainstorm's own entries — no bare names."
    - "Skipped categories (no artifact to check against yet) are listed explicitly, not left unmentioned."
  failure_conditions:
    - "FEATURES.md doesn't exist yet — escalate (per agents/gap-analysis-agent.md) rather than inventing a features list from scratch; that's Brainstorm's job."
```

See [ProjectFounder-idea.md](../../ProjectFounder-idea.md) (Section 7.8, Gap Analysis Engine; Section 10, Skills Engine; § 123 Step 8) for the full skill model this contract implements.
