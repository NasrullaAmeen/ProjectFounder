# Constraints

> **In plain terms:** hard rules this project's own idea already states, as opposed to `ASSUMPTIONS.md` (reasonable guesses). Written by `workflows/brainstorm.md`'s `discover` step against `examples/bookmark-manager/idea.md`.

- **Free to end users.** `idea.md` states "a free ... bookmark manager" — no paid tier is described; any architecture/budget work later must fit a $0-to-the-user model (§ 123 Step 13's "$0 architecture" scenario applies here directly, once Budget, Phase 5, exists).
- **Self-hosting must stay a real, supported deployment option, not the only one.** `idea.md`'s own wording is "optional self-hosting" — the hosted/cloud path is primary, but self-hosting can't be dropped as a deployment target (`PROJECT.yaml.types.deployment` already lists both `Cloud` and `Self-Hosted`).

## Conventions

- A constraint here should trace to `idea.md`'s own wording, not an inference — inferences belong in `ASSUMPTIONS.md` instead.
