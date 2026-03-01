<!-- Operational template: ai-toolkit/prompts/project-docs.md — keep in sync -->

# Cross-Project Conventions

Standards and patterns shared across [kphutt](https://github.com/kphutt) repositories.

## Project Documentation Lifecycle

Every repository follows the same documentation structure:

```
ROADMAP.md                              # root — prioritized big rocks
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

The PM view. Prioritized list of what's next. This *is* the backlog — no separate backlog file. Items are big rocks (features, refactors, architectural changes). Mark completed items with ~~strikethrough~~ and checkmark.

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

## CLAUDE.md Convention

Every repo has a `CLAUDE.md` at its root. This is the AI coding assistant's entry point — build commands, architecture overview, key patterns, testing notes, and a pointer to the docs structure.

Not a substitute for `README.md`. The README is for humans browsing GitHub. `CLAUDE.md` is for AI coding assistants that need to understand the codebase fast.

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
3. Add `CLAUDE.md` — architecture, build commands, conventions
4. Add `ROADMAP.md` — initial priorities
5. Create `docs/decisions/` and `docs/design/` directories
6. Optionally use [ai-toolkit](https://github.com/kphutt/ai-toolkit)'s `/bootstrap` skill to scaffold the structure

## What We Don't Do

- No separate backlog file — the roadmap is the backlog
- No decisions inside initiative folders — they're project-wide, not initiative-scoped
- No formal RFC process for solo/small team work — that's for collecting feedback from others
- No maintaining a decision index file — `ls docs/decisions/` is the index
