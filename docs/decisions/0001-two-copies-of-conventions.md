# Maintain two copies of the project-docs convention

## Status
Accepted

## Context

The project documentation convention (ROADMAP.md, docs/decisions/, docs/design/) needs to live somewhere accessible. Two audiences need it:

1. **Claude Code's `/bootstrap` skill** — needs it as an operational template to scaffold new projects. That template lives privately, alongside the skill.
2. **Humans browsing GitHub** — need a reference document explaining how all kphutt repos are organized. This belongs in the `.github` repo, which GitHub surfaces as default community health files.

The public copy (`.github`) must stand on its own and reference no private repository.

## Decision

We maintain two copies:
- a **private** operational template (used by `/bootstrap`)
- `.github/README.md` — the human-readable reference, the **standalone public source** (rendered on GitHub)

The public copy is self-contained. The private template is maintained privately; drift between the two is reconciled there, not via public cross-references.

## Consequences

- Either side can stand alone without broken references.
- The public conventions name or link no private repo.
- The convention is short (~60 lines) so keeping the copies in sync is low effort.
