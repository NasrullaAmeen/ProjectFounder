# Skill: discovery

> Ask only critical discovery questions about a classified project; unknown answers become assumptions or open questions, not blockers.

Status: Phase 1 (§ 140) — agent-executed, no code (see `docs/DECISIONS.md` D005). Invoked by `agents/discovery-agent.md` as the `discover` step of `workflows/brainstorm.md`.

## Contract

```yaml
skill:
  id: discovery
  version: 0.1.0
  purpose: "Ask only critical discovery questions about a classified project; unknown answers become assumptions or open questions, not blockers."
  inputs:
    - idea.md
    - PROJECT.yaml
  procedure:
    - "Derive the critical-question set from the idea and its PROJECT.yaml classification (§ 123 Step 4 style: primary users, mandatory vs. optional platform/deployment requirements, auth requirements, anything the idea states ambiguously) — don't ask generic filler questions unanswerable from the idea plus common sense."
    - "For each question, try to resolve it directly from the idea's own text first."
    - "If the idea's text doesn't answer it and a human is available in this session (AGENT.md's reasoning process: 'ask only critical discovery questions'), ask them directly rather than skipping straight to an assumption — this step only falls through to the next two when no interactive answer is available (e.g. a worked example run with no live user, or the human doesn't respond)."
    - "If still unanswered but a reasonable, low-risk default exists, resolve it as an assumption (ASSUMPTIONS.md) with its rationale and what breaks if it's wrong."
    - "If no reasonable default exists and the answer materially changes scope or architecture, resolve it as an open question (OPEN-QUESTIONS.md, § 111) instead of guessing."
    - "If the idea's own wording states a hard requirement (e.g. 'must be self-hosted'), record it as a constraint (CONSTRAINTS.md), not an assumption — constraints are stated, assumptions are inferred."
  tools: []
  outputs:
    - ASSUMPTIONS.md
    - CONSTRAINTS.md
    - OPEN-QUESTIONS.md
  validation:
    - "Every critical question asked has exactly one resolution: answered inline (no artifact needed), an ASSUMPTIONS.md entry, a CONSTRAINTS.md entry, or an OPEN-QUESTIONS.md entry — never left implicit."
    - "No question is resolved as both an assumption and an open question — that's a contradiction, not two independent facts."
  failure_conditions:
    - "idea.md is too sparse to derive any critical questions from — escalate (per agents/discovery-agent.md) rather than inventing generic questions with no connection to the actual idea."
```

See [ProjectFounder-idea.md](../../ProjectFounder-idea.md) (Section 7.2, Discovery Engine; Section 10, Skills Engine; § 123 Step 4) for the full skill model this contract implements.
