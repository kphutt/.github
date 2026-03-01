# Maintain two copies of the project-docs convention

## Status
Accepted

## Context

The project documentation convention (ROADMAP.md, docs/decisions/, docs/design/) needs to live somewhere accessible. Two audiences need it:

1. **Claude Code's `/bootstrap` skill** — needs it as an operational template to scaffold new projects. This template lives in `ai-toolkit/prompts/project-docs.md` alongside the other skills.
2. **Humans browsing GitHub** — need a reference document explaining how all kphutt repos are organized. This belongs in the `.github` repo, which GitHub surfaces as default community health files.

Moving the file to one location creates a cross-repo dependency. If someone clones ai-toolkit, they expect `/bootstrap` to work without cloning `.github` too. If someone visits `.github` on GitHub, they expect to read the conventions without navigating to another repo.

## Decision

We will maintain two copies:
- `ai-toolkit/prompts/project-docs.md` — the operational template (used by `/bootstrap`)
- `.github/README.md` — the human-readable reference (rendered on GitHub)

Each file has an HTML comment at the top pointing to the other copy. When the two diverge, `ai-toolkit` is the primary source — it's closer to the skill that enforces the convention.

## Consequences

- Either repo can be cloned standalone without broken references
- Drift is possible but mitigated by the cross-reference comments
- The convention is short (~60 lines) so keeping them in sync is low effort
- If the convention changes significantly, update ai-toolkit first, then propagate to .github
