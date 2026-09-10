# Skill: requirements

> Convert product intent and features into functional/non-functional requirements.

Status: Phase 1 (§ 140) — contract fleshed out, not yet exercised (see `agents/requirements-agent.md` for why: it refuses to run against an untiered `FEATURES.md`, and Feature Discovery's tiering isn't exercised yet either).

## Contract

```yaml
skill:
  id: requirements
  version: 0.1.0
  purpose: "Convert product intent and features into functional/non-functional requirements."
  inputs:
    - idea.md
    - PROJECT.yaml
    - FEATURES.md   # must be tiered
    - CONSTRAINTS.md
    - ASSUMPTIONS.md
  procedure:
    - "Read FEATURES.md's tiered candidates, starting with MVP — write requirements for MVP first; V1/V2/Future features get requirements only if the project explicitly wants them scoped this early."
    - "For each feature, write one or more requirements as REQ-<NNN>, numbered sequentially, each a single SHALL (mandatory) or SHOULD (recommended) statement (§ 123 Step 10's own REQ-001..004 wording), tagged with its type: functional, non-functional, technical, business, security, AI, or operational (§ 7.9)."
    - "Write acceptance criteria as GIVEN/WHEN/THEN wherever the requirement is checkable mechanically; classify each as executable (a check could exist under checks/) or judged (no mechanical check possible yet) — § 163.4."
    - "Trace every requirement back to the FEATURES.md entry (and, transitively, the idea/constraint) that motivated it — don't write a requirement with no traceable source."
    - "If a feature's rationale doesn't give enough to write a concrete requirement, don't force one — escalate per agents/requirements-agent.md instead."
  tools: []
  outputs:
    - REQUIREMENTS.md
  validation:
    - "Every MVP-tier feature has at least one requirement."
    - "Every requirement has an ID, a type tag, a SHALL/SHOULD statement, and acceptance criteria classified executable or judged (§ 163.4)."
    - "No requirement exists that doesn't trace back to a FEATURES.md entry."
  failure_conditions:
    - "FEATURES.md isn't tiered yet — escalate (per agents/requirements-agent.md) rather than writing requirements against undecided scope."
```

See [ProjectFounder-idea.md](../../ProjectFounder-idea.md) (Section 7.9, Requirements Engine; Section 10, Skills Engine; § 123 Step 10; § 163.4) for the full skill model this contract implements.
