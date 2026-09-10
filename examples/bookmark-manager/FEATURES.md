# Features

> **In plain terms:** every feature candidate this idea implies, tiered into MVP/V1/V2/Future. Written by `workflows/brainstorm.md`'s `brainstorm` step (draft candidates) and `workflows/requirements.md`'s `gap-analysis`/`feature-discovery` steps (added candidates + tiers) against `examples/bookmark-manager/idea.md`, `ASSUMPTIONS.md`, and `CONSTRAINTS.md`.

**Status: TIERED.** Gap Analysis (§ 7.8) added 8 candidates Brainstorm's draft pass missed; Feature Discovery (§ 7.7) then tiered all 24. Skipped categories with no owning artifact yet: architecture, security controls (beyond extension permissions, already feature-shaped), operational systems beyond what's listed, budget assumptions, and deployment considerations — none of those have an artifact to check against before Phase 3/5.

| Candidate | Tier | Why |
|---|---|---|
| Capture (save a link) | MVP | The core action the idea can't work without. |
| Search (keyword) | MVP | Baseline retrieval, needed alongside capture from day one. |
| Semantic Search | MVP | Explicitly the idea's own differentiator ("AI-powered ... semantic search"). |
| Organization (folders) | MVP | Needed once beyond a handful of bookmarks; a data-model decision that's expensive to retrofit later. |
| Import | MVP | Onboarding on-ramp — without it, nobody can move existing bookmarks in from a competitor. |
| Export | MVP | Pairs with Import; the self-hosting constraint's "way out" applies from day one, not later. |
| Authentication | MVP | Needed for the hosted path per `ASSUMPTIONS.md` A2 — can't ship the hosted product without it. |
| Sync | MVP | Idea offers web + PWA + extension together; without sync those are three silos, defeating the point. |
| Browser Extension | MVP | Explicitly named in `idea.md` alongside web/PWA as a core surface — resolves `OPEN-QUESTIONS.md` Q2. |
| Search indexing *(added by Gap Analysis)* | MVP | Semantic Search (already MVP) can't function without reliable indexing — a dependency of an MVP feature, not optional. |
| Extension permissions scoping *(added by Gap Analysis)* | MVP | If the extension is MVP, its permission scope is a manifest decision made when it ships, not deferrable. |
| Tags | V1 | A second organization axis; folders alone can ship the MVP. |
| Collections | V1 | Builds on organization; not day-one-critical. |
| PWA | V1 | Closely related to the MVP web app; PWA-specific packaging can follow shortly after. |
| Backup | V1 | Important, but the very first release can function without it briefly. |
| Self-hosting | V1 | `CONSTRAINTS.md` requires it exist as a real option eventually, not necessarily on day one — hosted-first ships faster. |
| Account deletion *(added by Gap Analysis)* | V1 | Legal/trust expectation; not core-value-blocking for a first release, but should follow quickly. |
| Data portability (standard format) *(added by Gap Analysis)* | V1 | Export (MVP) already gives an exit path; a documented standard format matters most once self-hosting (V1) makes cross-tool migration real. |
| Rate limiting *(added by Gap Analysis)* | V1 | Cost control matters once there's real hosted traffic; not needed for a small initial launch, but not safe to defer indefinitely given the "free" constraint. |
| AI Summaries | V2 | Adjacent nice-to-have; not stated in `idea.md`, no urgency signal. |
| Bookmark deduplication *(added by Gap Analysis)* | V2 | Quality-of-life; becomes relevant once a collection has accumulated imports, not at launch. |
| Broken link detection *(added by Gap Analysis)* | V2 | Same — collections have to age before link rot is a real problem. |
| Privacy controls (visibility) *(added by Gap Analysis)* | V2 | Default-private, single-tenant behavior already covers MVP; an explicit control matters once Sharing (below) is real. |
| Sharing | Future | Not stated in `idea.md`; no urgency signal, and nothing else depends on it yet. |

**Not added as separate candidates:** Gap Analysis's "AI cost" and "AI privacy" categories (§ 123 Step 8) are already tracked by `OPEN-QUESTIONS.md` Q1 (local vs. cloud AI) — that question *is* the cost/privacy tradeoff; a duplicate `FEATURES.md` entry would just restate it.

## Conventions

- A tier change (e.g. promoting a V1 to MVP) is a Feature Discovery re-run, not a manual edit — keep the reasoning traceable to whichever engine last touched a row.
