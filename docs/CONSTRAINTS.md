# Constraints

> **In plain terms:** these are the hard rules ProjectFounder's design is not allowed to break, as opposed to `ASSUMPTIONS.md` (things believed true but unverified) or `NON-GOALS.md` (things it deliberately won't attempt).

## Technology neutrality (§ 4.1 Technology Is Data)

ProjectFounder core must not be permanently coupled to:

- one programming language
- one database
- one AI provider
- one cloud provider
- one hosting provider
- one API
- one agent framework
- one MCP implementation
- one frontend framework

Technology choices route through the Resource model (`resources/`, `resource.schema.yaml`) — see `AGENTS.md` "Technology stays replaceable."

## Process constraints (`AGENTS.md`, `AGENT.md`)

- **Contracts before implementation.** Every engine/agent/skill/workflow/artifact has a documented contract before code is written against it.
- **Engines and artifacts stay separate.** An engine is code/logic; an artifact is the persisted output — never merged into one module.
- **No speculative generation.** Don't scaffold every possible document, agent, or workflow "just in case" (§ 139).
- **Follow the phase order.** New engine work follows § 140's Phase 0 → 8 sequence; don't jump ahead.
- **No silent overwrites.** A locked or human-approved artifact is never modified without surfacing the conflict through the Decision Engine (§ 106).
- **Human approval gates.** High-impact, hard-to-reverse actions (production deploys, financial commitments, major architecture changes) require human approval before proceeding.
- **Bounded retries.** Failures classify into retry / fallback / escalate / recover, with retry limits (§ 134) — never retry unboundedly.
- **No secrets in the repo.** Never commit API keys or credentials (`AGENTS.md` "Forbidden behavior").

## Content constraints

- **Evidence over assertion.** Research-sensitive facts (pricing, API limits, framework versions) carry source, confidence, and freshness (§ 36, § 37); web research is evidence to weigh, not automatic truth.
- **Surfaced uncertainty.** Unknowns become `OPEN-QUESTIONS.md` entries or documented assumptions — never hidden gaps (`AGENT.md` "Surface uncertainty").
- **No production-readiness claims without validation.** Readiness is reported explicitly (R0–R7, § 30); `AGENTS.md` forbids claiming an engine or project is "production ready" without passing the Final Quality Gates (§ 135).

## Conventions

- A constraint here should be traceable to a spec section or an `AGENTS.md`/`AGENT.md` rule — don't add house rules that aren't grounded in either.
- If a constraint needs to be relaxed, that's a spec amendment (see § 163 for the pattern), not a quiet edit to this file.
