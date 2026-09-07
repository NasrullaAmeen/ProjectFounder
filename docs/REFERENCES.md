# References

> **In plain terms:** this is where ProjectFounder's own external sources of evidence live — what was read, when, and why it's cited in the spec or a decision.

Per § 88, `REFERENCES.md` is a "Reference" document (§ 80: supporting information, not canonical). It indexes external sources; the full analysis lives in `docs/research/`.

## Primary research

- [`docs/research/2026-09-08-projectfounder-deep-research.md`](./research/2026-09-08-projectfounder-deep-research.md) — deep research on improving ProjectFounder (blogs, GitHub, Hacker News, Reddit), completed 2026-09-08. Source of the § 163 amendments; full source register in that file's § 5.

## Key external projects cited in the spec (§ 163)

Referenced as competitive/comparative context — not dependencies, not endorsed integrations:

- [github.com/github/spec-kit](https://github.com/github/spec-kit) — Spec-Driven Development tool; source of the "illusion of work" (#75) and readability (#4207) critiques behind § 163.1/§ 163.3.
- [github.com/Fission-AI/OpenSpec](https://github.com/Fission-AI/OpenSpec) — delta-spec (`changes/ → specs/ → archive`) model behind § 163.1; Explore workflow behind § 163.2.
- [martinfowler.com — "Understanding SDD: Kiro, spec-kit, and Tessl"](https://martinfowler.com/articles/exploring-gen-ai/sdd-3-tools.html) (Böckeler, 2025-10-15) — "specs, not code, are the primary artifact" framing.
- Hacker News item 45935763, "Spec-Driven Development: The Waterfall Strikes Back" — field critique synthesized across § 163.1–163.4.

## Conventions

- Add an entry here when a decision (`DECISIONS.md`) or spec amendment cites external evidence; link to the research file with the full analysis rather than re-summarizing it here.
- This file indexes sources — it does not restate their content. If the content matters, it belongs in `docs/research/`.
