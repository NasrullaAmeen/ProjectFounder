# Skill: brainstorm

> Expand a raw idea into possibilities, features, variants, and alternative approaches.

Status: Phase 1 (§ 140) — agent-executed, no code (see `docs/DECISIONS.md` D005). Invoked by `agents/brainstorm-agent.md` as the `brainstorm` step of `workflows/brainstorm.md`, after `skills/discovery/`'s `discover` step.

## Contract

```yaml
skill:
  id: brainstorm
  version: 0.1.0
  purpose: "Expand a raw idea into possibilities, features, variants, and alternative approaches."
  inputs:
    - idea.md
    - PROJECT.yaml
    - ASSUMPTIONS.md
    - CONSTRAINTS.md
  procedure:
    - "Read CONSTRAINTS.md and ASSUMPTIONS.md first — brainstorm within them, not against them (§ 123 Step 5 style)."
    - "Expand the idea into a broad candidate list: core-value features the idea can't work without, adjacent features implied by the idea's own wording, and standard infrastructure-level candidates (auth, sync, backup, import/export) where the classification suggests they'll matter."
    - "Write each candidate as one line: name plus a short one-clause rationale tying it back to the idea or a recorded assumption/constraint — no unexplained feature names."
    - "Do not categorize candidates into MVP/V1/V2/Future (§ 123 Step 9) — that tiering is the Feature Discovery Engine's job (§ 7.7), not this skill's, and isn't built yet."
    - "If a candidate would violate a CONSTRAINTS.md entry, leave it out and note the conflict rather than listing it as if it were viable."
  tools: []
  outputs:
    - FEATURES.md   # draft/uncategorized tier — see docs/DECISIONS.md D011
  validation:
    - "FEATURES.md is explicitly marked draft/uncategorized so it isn't mistaken for the Feature Discovery Engine's finished, tiered output."
    - "No listed candidate contradicts a CONSTRAINTS.md entry."
  failure_conditions:
    - "ASSUMPTIONS.md/CONSTRAINTS.md don't exist yet for this project — run skills/discovery/ first; this skill doesn't invent them itself."
```

See [ProjectFounder-idea.md](../../ProjectFounder-idea.md) (Section 7.3, Brainstorm Engine; Section 10, Skills Engine; § 123 Step 5) for the full skill model this contract implements.
