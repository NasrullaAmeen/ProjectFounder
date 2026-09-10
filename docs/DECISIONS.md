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

### D005 — Implement Phase 0 as agent-executed contracts, no code yet

```yaml
decision:
  id: D005
  title: Resolve docs/OPEN-QUESTIONS.md Q1 — Phase 0 stack choice
  context: >
    Phase 0 (§ 140: project model, manifest, schemas, configuration, state,
    lifecycle) needed an implementation approach before any of it could be
    built. AGENTS.md forbids inventing a stack unilaterally; this had to be
    surfaced as a decision.
  options:
    - TypeScript/Node.js (real code: schema validation, a small CLI, tests)
    - Python (real code, same scope)
    - Agent-only: Claude Code commands/skills/workflows read/write YAML and Markdown directly, validation is an agent reasoning over a schema file, no interpreter/runtime chosen yet
  selected: Agent-only, no code yet
  rationale: >
    Matches § 136 "smallest executable version of the architecture" and
    keeps § 4.1 (Technology Is Data) maximally intact — no language commits
    Phase 0 to an ecosystem before any engine actually needs deterministic
    logic an agent can't do by reading files and following instructions.
    Revisit once an engine needs real validation/state logic (see
    docs/OPEN-QUESTIONS.md Q2 for when that might be).
  evidence: N/A (architectural judgment call, not externally sourced)
  confidence: MEDIUM
  reversibility: MODERATE
  approval: RECOMMEND
  dependencies: [D004]
  affected_artifacts:
    - schemas/project.schema.yaml
    - config/lifecycle.yaml
    - config/project-types.yaml
    - agents/project-architect.md
    - workflows/new-project.md
    - commands/new-project.md
    - templates/core/PROJECT.yaml
```

### D006 — Add a classification escape hatch instead of extending § 28 or dropping labels

```yaml
decision:
  id: D006
  title: Resolve docs/OPEN-QUESTIONS.md Q9 — § 28 taxonomy gap found via the bookmark-manager example
  context: >
    Building examples/bookmark-manager/ showed that § 123's own canonical
    classification uses labels ("Search", "Data Platform", bare "AI",
    "Semantic Search") absent from § 28's five taxonomies. Left as-is, an
    agent classifying a project must either drop real information or
    silently invent a taxonomy value.
  options:
    - Extend § 28's enumerated lists to add the missing labels
    - Treat § 123's classification as loosely illustrative, not literal, and change nothing
    - Add a `types.other.<dimension>` free-text field alongside the enumerated one (§ 163.5)
  selected: Add the `other` escape hatch (§ 163.5)
  rationale: >
    Extending § 28 on the evidence of one project's labels risks taxonomy
    bloat from one-off terms (§ 139: "create unnecessary complexity").
    Treating § 123 as "just illustrative" quietly excuses the spec's own
    canonical example from matching its own taxonomy, which is worse than
    fixing it. `other` preserves information without touching § 28's
    enumerated list at all — recurring `other` labels become the evidence
    base for a future, deliberate § 28 amendment instead of one-off drift.
  evidence: examples/bookmark-manager/NOTES.md
  confidence: MEDIUM
  reversibility: EASY
  approval: RECOMMEND
  dependencies: []
  affected_artifacts:
    - "ProjectFounder-idea.md § 163.5"
    - schemas/project.schema.yaml
    - templates/core/PROJECT.yaml
    - workflows/new-project.md
    - examples/bookmark-manager/PROJECT.yaml
```

### D007 — Fold the P1 research recommendations into the spec as § 163.6/§ 163.7

```yaml
decision:
  id: D007
  title: Resolve docs/OPEN-QUESTIONS.md Q3 — session persistence and anti-drift amendments
  context: >
    docs/research/2026-09-08-projectfounder-deep-research.md's P1 items
    (context persistence across sessions, spec-kit #1482; an anti-drift
    loop, DZone/Focused Labs) had been logged as an open question rather
    than acted on, pending a decision on whether to fold them in now or
    wait for Phase 1/2 to make them concrete.
  options:
    - Wait until Phase 1/2 implementation makes Memory/Feedback engines concrete, amend the spec then
    - Fold both into the spec now as § 163.x amendments, same pattern as § 163.1-163.5
  selected: Fold in now
  rationale: >
    Both P1 items amend existing sections (§ 23, § 24, § 37, § 98, § 99,
    § 108, § 148) rather than requiring new engines to exist first - the
    § 163.1-163.5 amendments already established that a spec amendment can
    precede implementation. Waiting risks the same "sat on a completed,
    actionable finding" drift that motivated D003.
  evidence: docs/research/2026-09-08-projectfounder-deep-research.md § 4, items 5-6
  confidence: MEDIUM
  reversibility: MODERATE
  approval: RECOMMEND
  dependencies: [D003]
  affected_artifacts:
    - "ProjectFounder-idea.md § 163.6, § 163.7"
    - docs/OPEN-QUESTIONS.md
```

### D008 — Fold all four P2 research recommendations into the spec, not just the two logged

```yaml
decision:
  id: D008
  title: Resolve docs/OPEN-QUESTIONS.md Q4 — full P2 set, correcting an earlier triage gap
  context: >
    D003 originally triaged docs/research/2026-09-08-projectfounder-deep-research.md
    § 4 into P0/P1/P2 and only logged two of the four P2 items (§ 20
    "actions not phases" and the retrospective step) into
    docs/OPEN-QUESTIONS.md Q4 / docs/TASKS.md. The other two (evidence-forward
    positioning, autonomy-as-setting) were dropped in that pass and only
    surfaced again when asked to "keep going with the P2 items."
  options:
    - Only address the two items already tracked in Q4
    - Re-check the research report's full P2 list and address all four, noting the earlier gap
  selected: All four, gap noted
  rationale: >
    Silently completing only what was previously (incompletely) tracked
    would repeat the exact failure this repo's own docs/DECISIONS.md and
    OPEN-QUESTIONS.md exist to prevent - since the research findings were
    already recorded evidence (D003), leaving two of four unaddressed
    without even a tracked question would have been a gap nobody could see.
  evidence: docs/research/2026-09-08-projectfounder-deep-research.md § 4, items 7-10
  confidence: HIGH
  reversibility: MODERATE
  approval: RECOMMEND
  dependencies: [D003, D007]
  affected_artifacts:
    - "ProjectFounder-idea.md § 163.8, § 163.9, § 163.10, § 163.11"
    - config/lifecycle.yaml
    - schemas/project.schema.yaml
    - templates/core/PROJECT.yaml
    - examples/bookmark-manager/PROJECT.yaml
    - workflows/new-project.md
    - docs/OPEN-QUESTIONS.md
```

### D009 — Add an EXPLORING lifecycle state

```yaml
decision:
  id: D009
  title: Give § 163.2's Explore step a lifecycle state to land on
  context: >
    Exercising workflows/new-project.md against a second, non-CREATE-intent
    worked example (examples/notes-app-extend/) showed § 25's lifecycle
    diagram jumps straight from CLASSIFIED to DISCOVERY, with no state
    corresponding to § 163.2's EXPLORE step. A non-CREATE project had no
    valid way to record "Explore is happening now."
  options:
    - Reuse CLASSIFIED for the duration of Explore (stale — classification is actually done)
    - Let Explore advance straight to DISCOVERY (contradicts § 163.2's own instruction)
    - Add a new EXPLORING state between CLASSIFIED and DISCOVERY
  selected: Add EXPLORING (§ 163.12)
  rationale: >
    The other two options either misrepresent project state or directly
    contradict an already-approved amendment (§ 163.2). Adding one state
    is the smallest change that makes the § 163.2 diagram actually
    representable in PROJECT.yaml.
  evidence: examples/notes-app-extend/NOTES.md
  confidence: HIGH
  reversibility: EASY
  approval: AUTO_APPROVE
  dependencies: []
  affected_artifacts:
    - "ProjectFounder-idea.md § 163.12"
    - config/lifecycle.yaml
    - schemas/project.schema.yaml
    - workflows/new-project.md
```

### D010 — Add an intent-ambiguity escalation rule instead of an `intent_candidates` field

```yaml
decision:
  id: D010
  title: Give intent ambiguity an escalation path, without making `intent` multi-valued
  context: >
    Exercising workflows/new-project.md against a third worked example
    (examples/ambiguous-intent/, deliberately fitting REBUILD, MIGRATE, and
    EXTEND at once) showed the escalation contract only handled `types`
    ambiguity (an array field, via the § 163.5 `other`/"record all plausible
    values" pattern) and "intent is not CREATE" (which assumes intent has
    already resolved to one value). Nothing covered intent itself being
    ambiguous, and intent is schema-typed as a single string enum, so the
    § 163.5 pattern doesn't transfer directly.
  options:
    - Make `intent` an array (like `types`), recording every plausible candidate
    - Add an `intent_candidates` field alongside the existing single-valued `intent`
    - Keep `intent` single-valued; add an escalation rule that picks the closest fit and records rejected candidates + reasoning in the project's own OPEN-QUESTIONS.md
  selected: Keep `intent` single-valued; escalate via OPEN-QUESTIONS.md
  rationale: >
    Making `intent` an array would change what every existing consumer of
    the field (§ 163.2's Explore gate, § 163.12's lifecycle branch, the
    approvals gate in workflows/new-project.md) means by "the" intent, for
    a case that's rare relative to the churn of a schema change. An
    `intent_candidates` field would duplicate what OPEN-QUESTIONS.md (§ 111)
    already exists to hold, repeating the "generate every possible field"
    over-scoping § 139 forbids. The escalation-rule approach costs nothing
    schema-side and reuses an artifact that already has exactly this job.
  evidence: examples/ambiguous-intent/NOTES.md
  confidence: MEDIUM
  reversibility: EASY
  approval: RECOMMEND
  dependencies: []
  affected_artifacts:
    - "ProjectFounder-idea.md § 163.13"
    - agents/project-architect.md
    - workflows/new-project.md
    - examples/ambiguous-intent/PROJECT.yaml
```

### D011 — Reuse FEATURES.md as the Brainstorm Engine's draft-tier output, don't add a new artifact

```yaml
decision:
  id: D011
  title: Brainstorm writes an explicitly-uncategorized FEATURES.md, no separate BRAINSTORM.md
  context: >
    Building the Phase 1 Discovery+Brainstorm slice (workflows/brainstorm.md)
    needed a home for the Brainstorm Engine's raw candidate list (§ 123 Step 5).
    § 88 Core Project Artifacts already names FEATURES.md, but § 123 Step 9
    shows FEATURES.md's final shape is tiered (MVP/V1/V2/Future) by the
    Feature Discovery Engine (§ 7.7) - not yet built (deferred per the user's
    own Phase 1 scoping choice this round). Brainstorm's own output isn't
    tiered at all.
  options:
    - Add a new BRAINSTORM.md artifact for the raw candidate list, leave FEATURES.md for Feature Discovery to create later
    - Write the raw candidate list straight into FEATURES.md now, explicitly marked draft/uncategorized, for Feature Discovery to tier in place later
  selected: Write into FEATURES.md now, marked draft/uncategorized
  rationale: >
    A separate BRAINSTORM.md would duplicate what FEATURES.md is already
    specified to hold (§ 81 Documentation Deduplication) and repeats the
    "generate every possible document" over-scoping § 139 forbids. Writing
    into FEATURES.md directly, with an explicit draft/uncategorized marker
    so it isn't mistaken for Feature Discovery's finished, tiered output,
    keeps one canonical artifact that fills in incrementally as later
    engines run - the same incremental-artifact pattern § 163.7's Artifact
    Dependency Graph already assumes.
  evidence: workflows/brainstorm.md, skills/brainstorm/SKILL.md
  confidence: MEDIUM
  reversibility: EASY
  approval: RECOMMEND
  dependencies: []
  affected_artifacts:
    - agents/brainstorm-agent.md
    - skills/brainstorm/SKILL.md
    - workflows/brainstorm.md
    - examples/bookmark-manager/FEATURES.md
```

### D012 — Gap Analysis routes findings into existing artifacts, no new GAPS.md

```yaml
decision:
  id: D012
  title: Gap Analysis writes into FEATURES.md/OPEN-QUESTIONS.md by category, not a new artifact
  context: >
    Fleshing out agents/gap-analysis-agent.md needed a home for what the
    Gap Analysis Engine (§ 7.8) finds. § 88 Core Project Artifacts has no
    dedicated "GAPS.md," and § 7.8's own category list (requirements,
    features, documentation, architecture, security controls, operational
    systems, testing, budget assumptions, AI safeguards, deployment
    considerations) maps mostly onto artifacts that either already exist
    (FEATURES.md) or don't exist until later phases (ARCHITECTURE.md,
    BUDGET.md, Phase 3/5) - a single new artifact would either duplicate
    FEATURES.md or need placeholder sections for artifacts nothing else
    has built yet.
  options:
    - Add a new GAPS.md artifact covering all § 7.8 categories in one place
    - Route each found gap into whichever existing/future artifact already owns that category (FEATURES.md for feature-shaped gaps now; ARCHITECTURE.md/BUDGET.md/etc. once those exist), and OPEN-QUESTIONS.md for genuine unknowns
  selected: Route into existing artifacts by category
  rationale: >
    A new GAPS.md would violate § 81 Documentation Deduplication for the
    categories that already have a home (FEATURES.md) and would need
    placeholder sections for categories with no owning artifact yet,
    repeating the "generate every possible document" over-scoping § 139
    forbids. Routing by category keeps each artifact the single source of
    truth for its own domain, and naturally limits Gap Analysis's real
    scope today to what FEATURES.md/OPEN-QUESTIONS.md can actually hold -
    matching the phase-by-phase build order already established.
  evidence: agents/gap-analysis-agent.md, skills/gap-analysis/SKILL.md
  confidence: MEDIUM
  reversibility: EASY
  approval: RECOMMEND
  dependencies: [D011]
  affected_artifacts:
    - agents/gap-analysis-agent.md
    - skills/gap-analysis/SKILL.md
```

### D013 — Add a SCOPED lifecycle state instead of overloading RESEARCHING

```yaml
decision:
  id: D013
  title: Give Gap Analysis/Feature Discovery/Requirements a lifecycle state that doesn't overclaim Research happened
  context: >
    Wiring workflows/requirements.md (Gap Analysis -> Feature Discovery ->
    Requirements) against a DISCOVERY-lifecycle project hit the same shape
    of gap D009 already fixed once for EXPLORING: DISCOVERY's only legal
    next state in config/lifecycle.yaml is RESEARCHING, but this workflow
    doesn't do any research (§ 163.8 Actions, Not Phases already permits
    running it out of § 20's default order, since its own preconditions -
    lifecycle == DISCOVERY, a draft FEATURES.md - don't require Research).
    Setting lifecycle: RESEARCHING at the end would misrepresent that
    research happened; leaving it at DISCOVERY would be stale (real work
    happened).
  options:
    - Advance to RESEARCHING anyway, treating it loosely as "past Discovery"
    - Leave lifecycle at DISCOVERY, unchanged
    - Add a new SCOPED state, a second legal branch from DISCOVERY alongside RESEARCHING (mirroring D009's EXPLORING branch)
  selected: Add SCOPED (§ 163.14)
  rationale: >
    The first option makes RESEARCHING a lie; the second makes DISCOVERY
    stale despite three engines' worth of real output. Adding one state,
    in the same branching shape § 163.12 already established for EXPLORING,
    is the smallest change that lets PROJECT.yaml.lifecycle keep meaning
    what it says.
  evidence: workflows/requirements.md
  confidence: MEDIUM
  reversibility: EASY
  approval: RECOMMEND
  dependencies: [D009, D012]
  affected_artifacts:
    - "ProjectFounder-idea.md § 163.14"
    - config/lifecycle.yaml
    - schemas/project.schema.yaml
    - workflows/requirements.md
    - docs/OPEN-QUESTIONS.md
```

### D014 — Architecture requires REQUIREMENTS.md as an action precondition, not a lifecycle branch

```yaml
decision:
  id: D014
  title: Resolve Q10 — DESIGNING requires REQUIREMENTS.md regardless of which path reached RESEARCHING
  context: >
    § 163.14 (D013) left one thing unresolved: DISCOVERY can reach
    RESEARCHING either via SCOPED (Gap Analysis/Feature Discovery/
    Requirements already ran) or directly (skipping them). If entered
    directly, should DESIGNING still require SCOPED's REQUIREMENTS.md,
    given agents/architecture-agent.md already says it designs "from
    validated requirements"? Left open pending Phase 2/3 since it wasn't
    testable without those engines existing.
  options:
    - Leave it unresolved until Phase 2/3 implementation forces the question
    - Add a third lifecycle branch/state distinguishing "RESEARCHING with requirements" from "RESEARCHING without"
    - Make REQUIREMENTS.md a precondition on the DESIGNING/Architecture action itself, independent of lifecycle state
  selected: Precondition on the action (§ 163.15)
  rationale: >
    A new lifecycle state would encode a fact about action history (did
    Requirements run yet) into the state machine, which § 163.8 Actions,
    Not Phases already argues against - preconditions belong on actions,
    not states. architecture-agent.md's purpose already names "validated
    requirements" as a hard input, so the precondition mirrors the existing
    pattern in product-agent.md's escalation (do not run without its
    required upstream artifact) rather than inventing new state-machine
    shape. Resolving now (cheap, no code yet) also avoids deciding it
    implicitly while drafting research-agent.md's input contract in Phase 2.
  evidence: agents/architecture-agent.md purpose line; agents/product-agent.md escalation pattern
  confidence: MEDIUM
  reversibility: EASY
  approval: RECOMMEND
  dependencies: [D013]
  affected_artifacts:
    - "ProjectFounder-idea.md § 163.15"
    - agents/architecture-agent.md
    - config/lifecycle.yaml
    - docs/OPEN-QUESTIONS.md
    - docs/TASKS.md
```

## Conventions

- Add a new `D0NN` entry per decision that would be non-obvious from the diff alone — not for every commit.
- Never edit a past decision's `selected`/`rationale` after the fact; if a decision is reversed, add a new decision that supersedes it and note that in `dependencies`.
