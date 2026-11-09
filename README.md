# Cross-Project Conventions

Standards and patterns shared across [kphutt](https://github.com/kphutt) repositories.

## Project Documentation Lifecycle

Every repository follows the same documentation structure:

```
ROADMAP.md                              # root — prioritized big rocks
BACKLOG.md                              # root — new repos only: Blocked / In progress / Done
archive/
  done-YYYY-MM.md                       # new repos only: older Done entries, one file per month
docs/
  decisions/
    0001-short-title.md                 # one decision per file
    0002-short-title.md
  design/
    {initiative}/
      brainstorm.md                     # required scratchpad per initiative
```

**Lifecycle:** Roadmap item &rarr; brainstorm &rarr; decisions &rarr; code

## ROADMAP.md

The PM view. Prioritized list of what's next. It is the plan, not the work queue. In a new repo, open work lives in `BACKLOG.md`; in an existing repo, in the issue tracker. Items are big rocks (features, refactors, architectural changes). Mark completed items with ~~strikethrough~~ and checkmark.

## BACKLOG.md (new repos)

New repos keep open work in a root `BACKLOG.md` with three sections: Blocked, In progress and Done. When Done grows long, move its older entries to `archive/done-YYYY-MM.md`, one file per month. Write it as curated public content, since every repo is assumed to go public one day: no local paths, no personal data, no private tracker links, no unfixed security findings.

Existing repos keep their issue tracker. They are not migrated, and they get no `BACKLOG.md`. A next step that stays open after a commit goes to the backlog (the tracker, or `BACKLOG.md` in a new repo), never into the commit message.

## Decision Records (`docs/decisions/`)

One file per decision, numbered sequentially (`0001`, `0002`, ...). Append-only — never edit after writing. If a decision is reversed, write a new record that supersedes it.

### Template

```markdown
# Short title (verb phrase)

## Status
Accepted | Superseded by 0042

## Context
What's the situation? What forces are at play? Value-neutral facts.

## Decision
What did we decide? "We will..." in active voice.

## Consequences
What follows from this — good, bad, and neutral.
```

### When to write one

- You chose between alternatives (language, library, architecture)
- You discovered something surprising that changed your approach
- You'd be annoyed if future-you had to re-derive the reasoning
- You wouldn't — skip it. Not every choice needs a record.

## Initiative Brainstorms (`docs/design/{name}/brainstorm.md`)

Required for every initiative. Dump sub-tasks, open questions, half-baked ideas, trade-off analysis before building. Messy by design. When something settles, it graduates to a decision record in `docs/decisions/`.

## AGENTS.md Convention

Every repo has an `AGENTS.md` at its root — the tool-agnostic ([agents.md](https://agents.md)) entry point that AI coding assistants read: build commands, architecture overview, key patterns, testing notes, and a pointer to the docs structure.

Not a substitute for `README.md`. The README is for humans browsing GitHub. `AGENTS.md` is for AI coding assistants that need to understand the codebase fast.

## Commit Style

Imperative mood, present tense. First line is a concise summary (under 72 characters). The subject describes the change, not the file.

Examples:
- `Add combat initiative development backlog`
- `Fix remove_link failing on symlinks to directories`
- `Implement Phase 3: Header Screener and Rules engine`

No conventional-commits prefix (`feat:`, `fix:`) — just clear English.

## Bootstrapping a New Project

1. Create the repo and clone it
2. Add `README.md` — what it is, how to use it
3. Add `AGENTS.md` — architecture, build commands, conventions
4. Add `ROADMAP.md` — initial priorities
5. Create `docs/decisions/` and `docs/design/` directories

## What We Don't Do

- No second project-level backlog file: new repos use `BACKLOG.md` only, and existing repos use their tracker
- No decisions inside initiative folders — they're project-wide, not initiative-scoped
- No formal RFC process for solo/small team work — that's for collecting feedback from others
- No maintaining a decision index file — `ls docs/decisions/` is the index
