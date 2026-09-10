# Features

> **In plain terms:** this is a draft, uncategorized list of feature candidates the idea implies — nobody has decided yet what's MVP versus later. Written by `workflows/brainstorm.md`'s `brainstorm` step (§ 7.3 Brainstorm Engine) against `examples/bookmark-manager/idea.md`, `ASSUMPTIONS.md`, and `CONSTRAINTS.md`.

**Status: DRAFT / UNCATEGORIZED.** Not yet tiered into MVP/V1/V2/Future (§ 123 Step 9) — that's the Feature Discovery Engine's job (§ 7.7), not yet built (see `docs/DECISIONS.md` D011). Nothing below should be read as scoped or committed.

| Candidate | Why it's here |
|---|---|
| Capture (save a link) | The core action the idea can't work without. |
| Organization (folders) | Needed once a user has more than a handful of saved links. |
| Tags | Idea's own "organization" implies more than one axis of grouping; tags are the standard second axis alongside folders. |
| Collections | Groups of related bookmarks for a topic/project — a common bookmark-manager primitive the idea's "organization" implies. |
| Search (keyword) | Baseline retrieval; semantic search (below) builds on top of it, doesn't replace it. |
| Semantic Search | Explicitly named in `idea.md` (`RAG`/`Semantic Search` in `PROJECT.yaml`'s classification). |
| AI Summaries | Natural extension once AI is already in the architecture for semantic search — not stated in `idea.md`, included as a plausible adjacent capability, not a commitment. |
| Browser Extension | Explicitly named in `idea.md`; MVP inclusion is `OPEN-QUESTIONS.md` Q2. |
| PWA | Explicitly named in `idea.md`. |
| Import | Standard on-ramp for a bookmark manager — without it, switching from an existing tool has no path in. |
| Export | Pairs with Import; also supports `CONSTRAINTS.md`'s self-hosting requirement — self-hosters need a way out, not just in. |
| Sharing | Common bookmark-manager feature (public/shared collections); not stated in `idea.md`, included as a plausible candidate only. |
| Authentication | Needed for the hosted path per `ASSUMPTIONS.md` A2. |
| Sync | Implied by the idea offering web app + PWA + browser extension together — the same bookmarks need to appear in all three. |
| Backup | Standard operational concern for anything storing user data long-term; sharper for the self-hosted deployment path (`CONSTRAINTS.md`). |
| Self-hosting | Explicitly named in `idea.md` as optional; `CONSTRAINTS.md` says it must stay a real option. |

## Conventions

- Don't add a tier column here manually — that's Feature Discovery's output, not Brainstorm's. Adding one now would misrepresent how far this artifact has actually gotten.
