# Assumptions

> **In plain terms:** these are things the spec and this repo currently take for granted but haven't proven or decided outright. If one of these turns out false, expect ripple effects across the sections listed.

Unproven premises the design currently relies on. When an assumption is invalidated, record that as a new entry in `DECISIONS.md`, not a silent edit here.

| # | Assumption | Relied on by | Confidence |
|---|---|---|---|
| A1 | ProjectFounder's output is consumed by a coding agent (Claude Code, Codex, Cursor, or similar), not read/executed by a human-only process. | README "What is ProjectFounder?"; § 98 Build Context Package; § 99 Handoff System | HIGH — stated directly in the README |
| A2 | A project can be fully represented as a directory of Markdown + YAML artifacts (no binary/proprietary project-state format). | § 6.2 Artifacts; § 88 Core Project Artifacts; § 121 Machine-Readable Artifacts | HIGH — this is the artifact model itself |
| A3 | A human is available, synchronously or near-synchronously, to clear approval gates (`REQUIRE_HUMAN_APPROVAL`, artifact locks). | § 34 Decision Engine; § 106 Artifact Locking; `AGENT.md` "Human approval gates" | MEDIUM — no async/offline approval flow is specified |
| A4 | Whichever agent runs the Research Engine has live web/GitHub search and fetch access. | § 7.4 Research Engine; § 36 Evidence Model; § 37 Research Freshness | MEDIUM — true for Claude Code with WebSearch/WebFetch, not guaranteed for every adapter |
| A5 | Git (or an equivalent VCS) is the underlying version control for both this repo and any project ProjectFounder manages. | § 108 Change Management; § 128 Versioning; this repo's own `.git` | HIGH — implicit throughout, never stated as a hard requirement |
| A6 | "Technology is data" (§ 4.1) holds even for ProjectFounder's own implementation stack once chosen — i.e. Phase 0's stack choice shouldn't get hard-baked into engine contracts. | § 4.1 Technology Is Data; `AGENTS.md` "Technology stays replaceable" | MEDIUM — untested, no engine code exists yet to confirm |
| A7 | One project = one directory under `output/<project>/`; multi-repo / polyrepo projects are out of scope for v0.1. | § 122 Project Output Structure | MEDIUM — not discussed either way in the spec |

## Conventions

- An assumption graduates to a `CONSTRAINTS.md` entry once it's deliberately locked in, or to `OPEN-QUESTIONS.md` if it needs to be resolved rather than just tracked.
- Cite the section(s) that would break if the assumption is wrong, not just where it's used.
