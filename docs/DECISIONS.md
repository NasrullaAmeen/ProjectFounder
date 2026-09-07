# Decisions

> **In plain terms:** this is the log of real choices made while building ProjectFounder itself, why each one was made, and how reversible it is. It exists so nobody has to reverse-engineer "why is it like this" from the diff history.

Uses the Decision Engine record shape (`ProjectFounder-idea.md` § 34). This file is this repo's own decision log — the same model ProjectFounder's Decision Engine will eventually apply to downstream projects, applied here first.

---

### D001 — Adopt the v0.1 scaffold structure as specified

```yaml
decision:
  id: D001
  title: Ship the repo as a spec-first scaffold before any engine code
  context: >
    ProjectFounder needed a starting shape: either write engine code first and
    infer the spec from it, or write the full spec and scaffold contracts
    against it before implementing anything.
  options:
    - Code-first: build one engine, let the spec follow
    - Spec-first: write the full spec, scaffold contracts/schemas as drafts, defer engine code
  selected: Spec-first
  rationale: >
    AGENTS.md's "the spec is canonical" rule only works if the spec exists
    before the code that's supposed to trace back to it.
  evidence: N/A (founding decision, no external evidence gathered)
  confidence: HIGH
  reversibility: MODERATE
  approval: AUTO_APPROVE
  dependencies: []
  affected_artifacts: [ProjectFounder-idea.md, AGENT.md, AGENTS.md, CLAUDE.md]
```

### D002 — Separate this repo's own docs from downstream project artifacts

```yaml
decision:
  id: D002
  title: Add docs/ for ProjectFounder's own documentation, distinct from output/<project>/
  context: >
    ProjectFounder generates canonical artifacts (SPEC.md, TASKS.md, ...) for
    downstream projects it manages (§ 88, § 122). This repo also needs its own
    changelog/backlog/research, and reusing the same filenames at the repo
    root risked confusing "ProjectFounder's own TASKS.md" with the TASKS.md
    artifact the spec defines for a generated project (§ 91).
  options:
    - Keep CHANGELOG.md etc. at repo root, add a plain TASKS.md alongside
    - Put this repo's own docs under docs/, explicitly separate from output/<project>/
  selected: docs/ directory, explicitly separate from output/<project>/
  rationale: >
    Keeps the artifact model's meaning intact: output/<project>/TASKS.md is a
    generated artifact owned by the Task Engine; docs/TASKS.md is a
    hand-maintained backlog for this repo. Same filename, different owners,
    would violate Documentation Deduplication (§ 81) in spirit if collocated.
  evidence: N/A
  confidence: HIGH
  reversibility: EASY
  approval: AUTO_APPROVE
  dependencies: []
  affected_artifacts: [README.md, docs/README.md, docs/CHANGELOG.md, docs/TASKS.md, "ProjectFounder-idea.md § 145"]
```

### D003 — Adopt the § 163 v0.1.1 spec amendments

```yaml
decision:
  id: D003
  title: Fold P0 research recommendations into the spec as called-out amendments
  context: >
    docs/research/2026-09-08-projectfounder-deep-research.md surveyed the
    spec-driven-development field (spec-kit, OpenSpec, HN, Reddit) and found
    four P0 gaps against incumbents and field critique.
  options:
    - Leave the research as a standalone report, revisit later
    - Fold the P0 items into ProjectFounder-idea.md now, as explicit amendments
  selected: Fold into the spec now, as § 163 (delta-spec mode, explore-before-design, human-readable tier, executable validation)
  rationale: >
    AGENTS.md requires the spec to stay canonical and current; sitting on a
    completed, actionable research report unactioned is itself a form of
    drift. Amendments are additive and cross-referenced rather than rewriting
    existing sections, so nothing already-decided gets silently changed.
  evidence: docs/research/2026-09-08-projectfounder-deep-research.md § 4 (Recommendations), § 5 (Source Register)
  confidence: MEDIUM
  reversibility: MODERATE
  approval: RECOMMEND
  dependencies: [D001]
  affected_artifacts: ["ProjectFounder-idea.md § 163", docs/CHANGELOG.md, docs/TASKS.md]
```

### D004 — Scope this repo's own Core Project Artifacts (§ 88) to what has real content today

```yaml
decision:
  id: D004
  title: Create only the § 88 artifacts fillable without a pending decision
  context: >
    § 88 lists the full artifact set a ProjectFounder project "should
    normally contain." Applying it wholesale to this repo (as ProjectFounder's
    own first project) would mean writing TECH-STACK.md, ARCHITECTURE.md,
    BUDGET.md, ROADMAP.md, REQUIREMENTS.md, and FEATURES.md before the
    decisions they depend on (starting with the implementation stack, still
    open — see OPEN-QUESTIONS.md) have actually been made.
  options:
    - Generate the full § 88 list now, marking unresolved ones as draft/blocked
    - Generate only DECISIONS.md, ASSUMPTIONS.md, CONSTRAINTS.md, NON-GOALS.md, OPEN-QUESTIONS.md, LIMITATIONS.md, REFERENCES.md now
  selected: The narrower set with real content today
  rationale: >
    § 139 explicitly forbids "generate every possible document" and "create
    unnecessary complexity." Placeholder ARCHITECTURE.md/BUDGET.md/ROADMAP.md
    would be exactly the "illusion of work" critique the research report
    (and § 163.1/§ 163.4) warns about.
  evidence: "ProjectFounder-idea.md § 139"
  confidence: HIGH
  reversibility: EASY
  approval: AUTO_APPROVE
  dependencies: [D003]
  affected_artifacts: [docs/DECISIONS.md, docs/ASSUMPTIONS.md, docs/CONSTRAINTS.md, docs/NON-GOALS.md, docs/OPEN-QUESTIONS.md, docs/LIMITATIONS.md, docs/REFERENCES.md]
```

## Conventions

- Add a new `D0NN` entry per decision that would be non-obvious from the diff alone — not for every commit.
- Never edit a past decision's `selected`/`rationale` after the fact; if a decision is reversed, add a new decision that supersedes it and note that in `dependencies`.
