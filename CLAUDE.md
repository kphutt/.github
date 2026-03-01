# .github — Conventions

Cross-project conventions, templates, and default community health files for [kphutt](https://github.com/kphutt) repositories.

## What this repo is

GitHub's [default community health files](https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/creating-a-default-community-health-file) feature: files here apply as defaults across all kphutt repos that don't have their own versions.

## Relationship to ai-toolkit

The project documentation conventions in `README.md` are a human-readable reference copy. The operational template lives in [`ai-toolkit/prompts/project-docs.md`](https://github.com/kphutt/ai-toolkit/blob/main/prompts/project-docs.md) and is used by the `/bootstrap` skill. When the two diverge, ai-toolkit is the primary source.

See `docs/decisions/0001-two-copies-of-conventions.md` for the full rationale.

## Project docs

This repo follows its own convention:

- `ROADMAP.md` — priorities for this repo
- `docs/decisions/` — decision records
- `docs/design/` — initiative brainstorms
