# Notes: running workflows/new-project.md against the bookmark-manager idea

This directory is the first real exercise of `workflows/new-project.md` (`docs/TASKS.md`: "Exercise workflows/new-project.md on a real idea end-to-end and fix whatever the contract gets wrong in practice"). Input: the canonical idea from `ProjectFounder-idea.md` § 123 Step 1. Output: `idea.md` and `PROJECT.yaml` in this directory.

## What worked

- Capture (step 1) was mechanical: slug the idea into an `id`, name it, set `created_at`/`updated_at`, `lifecycle: CAPTURED`.
- The `intent: CREATE` default held — nothing about the idea suggested otherwise.
- `complexity: HIGH` was a reasonable initial call given multiple client surfaces (web, PWA, browser extension) plus AI/RAG plus an optional self-hosting deployment target — exactly the kind of "first guess, refine later" the workflow calls for.
- The lifecycle transition `CAPTURED -> CLASSIFIED` matched `config/lifecycle.yaml` with no ambiguity.

## What broke: § 123's own example doesn't match § 28's taxonomy

Step 3 of § 123 gives this classification for the bookmark manager:

```text
Product: SaaS, Freemium, Open Source candidate
Application: Web, PWA, Browser Extension
Technical: Search, Data Platform
AI: AI, RAG, Semantic Search
Deployment: Cloud, Self-Hosted
```

Checked against `config/project-types.yaml` (which is copied verbatim from § 28):

| § 123's label | Dimension | In § 28 / config/project-types.yaml? |
|---|---|---|
| SaaS, Freemium | Product | Yes |
| "Open Source candidate" | Product | Close — § 28 has `Open Source`, not `"...candidate"` (a confidence qualifier, not a taxonomy value) |
| Web, PWA, Browser Extension | Application | Yes |
| Search | Technical | **No** — not in the Technical dimension's 8 values |
| Data Platform | Technical | **No** — closest is `Platform`, but "Data Platform" isn't a listed value |
| AI | AI | **No** — the AI dimension has no bare `AI` value (closest: `AI SaaS`, `AI API`) |
| RAG | AI | Yes |
| Semantic Search | AI | **No** — not a listed value |
| Cloud, Self-Hosted | Deployment | Yes |

Originally, this `PROJECT.yaml` used only real `config/project-types.yaml` values — `technical: [Platform]`, `ai: [RAG]` — dropping "Search," "Data Platform," "AI," and "Semantic Search" because § 28's taxonomy had no slot for them.

## Resolved: § 163.5 Classification Escape Hatch

Rather than extending § 28's enumerated list unilaterally (silent drift) or continuing to drop the information, `ProjectFounder-idea.md` § 163.5 adds a `types.other.<dimension>` free-text field. This `PROJECT.yaml` now carries `other.technical: [Search, "Data Platform"]` and `other.ai: [AI, "Semantic Search"]` — the enumerated values stay exactly as § 28 specifies, and nothing from the original idea's classification is lost. `docs/OPEN-QUESTIONS.md` Q9 is resolved to this; `docs/DECISIONS.md` D006 has the full rationale.

## Fixed vs. not fixed

- **Fixed**: `schemas/project.schema.yaml` and `templates/core/PROJECT.yaml` were missing `created_at`/`updated_at`, even though § 123 Step 2 says capture creates one and § 148 requires both on every artifact. Added both — see `docs/CHANGELOG.md`.
- **Fixed**: the § 28 / § 123 taxonomy mismatch, via the § 163.5 escape hatch above.

## Takeaway

The capture/classify/validate mechanics in `workflows/new-project.md` held up on first exercise. Both gaps this exercise surfaced were spec-level (a missing artifact field, a taxonomy that didn't cover its own canonical example) rather than workflow-procedure bugs — which is the value of actually running a worked example instead of only reading the contracts.

---

# Notes: running workflows/brainstorm.md (Phase 1 — Discovery + Brainstorm)

Second exercise of this directory, now testing the first Phase 1 workflow against the same project (`docs/TASKS.md`: exercise `workflows/brainstorm.md` end-to-end). Input: this directory's existing `idea.md` and `PROJECT.yaml` (lifecycle `CLASSIFIED`, intent `CREATE`). Output: `ASSUMPTIONS.md`, `CONSTRAINTS.md`, `OPEN-QUESTIONS.md`, `FEATURES.md` added to this directory; `PROJECT.yaml` advanced to lifecycle `DISCOVERY`.

## What worked

- The precondition check was clean: `lifecycle: CLASSIFIED` and `intent: CREATE` both held, so the workflow proceeded without needing the (unimplemented) Explore step.
- Discovery's critical-question derivation followed § 123 Step 4's own canonical question set for this exact idea (who are the users, is self-hosting mandatory, should AI work locally, is the browser extension required for MVP, is auth required) — each resolved cleanly into exactly one of an inline answer (self-hosting: idea says "optional," so hosted is primary and self-hosting must stay a real option — `CONSTRAINTS.md`), an assumption (`ASSUMPTIONS.md` A1/A2), or an open question (`OPEN-QUESTIONS.md` Q1/Q2) — no question ended up with zero or more than one resolution.
- Brainstorm's candidate list matched § 123 Step 5's own canonical list for this idea almost exactly (Capture, Organization, Tags, Collections, Search, Semantic Search, AI Summaries, Browser Extension, PWA, Import, Export, Sharing, Authentication, Sync, Backup, Self-hosting) — confirming that "adjacent, not literally stated" candidates (AI Summaries, Sharing) are within scope for Brainstorm, not a "no speculative generation" (`AGENTS.md`) violation, since the spec's own canonical worked example already includes them.
- No candidate contradicted a `CONSTRAINTS.md` entry, so `agents/brainstorm-agent.md`'s "drop and note" escalation rule never fired on this run — untested by this exercise.
- The lifecycle transition `CLASSIFIED -> DISCOVERY` matched `config/lifecycle.yaml` with no ambiguity.

## What broke: the discovery procedure skipped straight past "ask the human"

`AGENT.md`'s own reasoning process says "ask only critical discovery questions; let unanswered questions become assumptions/open questions" — which implies the agent should actually ask a live user the critical questions first, and only fall back to an assumption or open question when no interactive answer is available. The first draft of `skills/discovery/SKILL.md`'s procedure skipped that step entirely: idea text first, then straight to assumption-or-open-question, with no step in between for actually asking anyone. That happened to be harmless for *this* exercise (a worked example with no live user to ask, exactly the fallback case), but would have been wrong for a real interactive session — it would silently guess or park a question as "open" instead of just asking, which is worse than either.

## Fixed: added the missing interactive-ask step

`skills/discovery/SKILL.md`'s procedure now reads: idea text first → ask the human directly if one is available in-session → assumption if a low-risk default exists → open question otherwise. The fallback-only case (no live user, e.g. this worked example) still works exactly as before.

## Takeaway

Same pattern as the Phase 0 exercises: the workflow's own step sequence (precondition-check → discover → brainstorm → advance-lifecycle) held up fine, and the real gap was one level down, in a skill's procedure that under-specified how a step actually resolves in the common case (a live user) versus the edge case (no user) it happened to be tested against first. Worth remembering for the next Phase 1 slice (Requirements/Feature Discovery/Gap Analysis): check that a procedure's steps make sense for *both* an interactive run and an offline worked-example run, not just whichever one gets exercised first.

---

# Notes: running workflows/requirements.md (Phase 1 — Gap Analysis + Feature Discovery + Requirements)

Third exercise of this directory: Gap Analysis → Feature Discovery → Requirements against the `DISCOVERY`-lifecycle project `workflows/brainstorm.md` left behind. Input: this directory's `FEATURES.md` (draft, 16 candidates), `CONSTRAINTS.md`, `ASSUMPTIONS.md`, `OPEN-QUESTIONS.md`. Output: `FEATURES.md` gap-filled (24 candidates) and fully tiered; `REQUIREMENTS.md` added (11 MVP requirements); `OPEN-QUESTIONS.md` Q2 resolved; `PROJECT.yaml` advanced to lifecycle `SCOPED`.

## What worked

- The precondition check was clean: `lifecycle: DISCOVERY` and an existing draft `FEATURES.md` both held.
- Gap Analysis's 8 new candidates matched § 123 Step 8's own canonical gap list for this exact idea almost one-for-one (Account deletion, Bookmark deduplication, Broken links, Privacy, Search indexing, Data portability, Extension permissions, Rate limits) — with two exceptions, "AI cost" and "AI privacy," which were already covered by `OPEN-QUESTIONS.md` Q1 (local vs. cloud AI) rather than needing a duplicate `FEATURES.md` entry. That's `skills/gap-analysis/SKILL.md`'s "gap-check against what's already there, don't re-derive" instruction working as intended — the first real test of it not just adding everything the canonical list mentions without checking for overlap first.
- Feature Discovery's MVP/V1/V2/Future tiering doubled as the resolution for `OPEN-QUESTIONS.md` Q2 ("is the browser extension required for MVP?") — tiering it MVP *was* answering that question, not a separate step. Worth noting for future runs: Feature Discovery should always check whether an open question is actually "which tier does this land in" in disguise before treating it as still open.
- Requirements produced one `REQ-<NNN>` per MVP feature (11 total) cleanly, each traceable to a `FEATURES.md` row; 3 of 11 ended up `judged` rather than `executable` (§ 163.4) because the check they'd need — relevance quality, a specific indexing-latency bound, an automated manifest-permission scan — doesn't exist yet, not because the requirement itself was ambiguous.
- `agents/product-agent.md`'s "mark provisional if competitive positioning needs unavailable research" escalation never fired — every tier call in this run was decidable from internal signals (the idea, constraints, assumptions) alone. Still untested: an idea where a tier call genuinely can't be made without knowing what competitors already do.

## What broke: DISCOVERY had nowhere honest to go

Wiring `workflows/requirements.md` hit the same shape of gap `examples/notes-app-extend/NOTES.md` (§ 163.12, `EXPLORING`) found once already: `config/lifecycle.yaml`'s only legal next state from `DISCOVERY` was `RESEARCHING`, but this workflow does no research. Setting `lifecycle: RESEARCHING` at the end would have overclaimed research happened; leaving it at `DISCOVERY` would understate three engines' worth of real output.

## Fixed: § 163.14 adds a SCOPED lifecycle state

Added `SCOPED` as a second legal branch from `DISCOVERY` (alongside `RESEARCHING`), landed on when Gap Analysis/Feature Discovery/Requirements run before Research — licensed by § 163.8 Actions, Not Phases, which already permits running an action out of § 20's default order as long as its own preconditions hold. Left deliberately open: whether `DESIGNING` should still require `SCOPED`'s `REQUIREMENTS.md` even when a project reaches `RESEARCHING` the other way (straight from `DISCOVERY`, skipping this workflow) — logged as `docs/OPEN-QUESTIONS.md` Q10 rather than guessed at, since neither Research nor Architecture is built yet to actually test it against. See `docs/DECISIONS.md` D013.

## Takeaway

Third exercise, same underlying lesson as the first two: the workflow's own step sequence held up, and the real gap was in the lifecycle model underneath it — specifically, that § 163.8's "actions can run out of order" license doesn't automatically give the lifecycle state machine anywhere to represent having done so. Two of these gaps now (`EXPLORING`, `SCOPED`) share the same shape: a real, reachable project condition with no state to land on. Worth checking proactively next time a new workflow is wired, rather than waiting to hit it.
