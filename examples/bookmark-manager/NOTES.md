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
