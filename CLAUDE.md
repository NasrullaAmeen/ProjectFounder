# CLAUDE.md — Claude Code Adapter

This file adapts the generic [`AGENT.md`](./AGENT.md) / [`AGENTS.md`](./AGENTS.md) contracts to Claude Code conventions when Claude Code works in this repository.

## Context

This repository is ProjectFounder itself (see `README.md` and `ProjectFounder-idea.md`), currently a v0.1 scaffold. When asked to "build ProjectFounder" or extend it, treat `ProjectFounder-idea.md` as the spec and `AGENTS.md` as the house rules.

When Claude Code is asked to **run ProjectFounder against a new idea** (i.e. act as the system, not develop it), follow `AGENT.md` instead — that's the operating contract for the intelligence system itself.

## Claude Code-specific notes

- Prefer editing existing stub files under `agents/`, `skills/`, `schemas/`, `config/` over creating new parallel ones — each already has a contract shape from the spec (§§ 150–152).
- When implementing an engine, check `ProjectFounder-idea.md` for its section number and keep the implementation traceable back to it (link the section in comments/docs sparingly, only where non-obvious).
- Use the `output/` directory as the target for any project ProjectFounder generates; never write generated project output into the repo root.
- This repo has no build/test tooling yet (v0.1 scaffold). Don't invent a stack (language, framework, package manager) unilaterally — surface the choice as a decision (spec § 34, Decision Engine) before committing to it, since it will shape every engine implementation that follows.

## Future adapters

Other coding-agent adapters (`CODEX.md`, `GEMINI.md`, `CURSOR.md`, etc.) should only be added when actually needed (spec § 89).
