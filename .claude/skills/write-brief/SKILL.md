---
name: write-brief
description: Write a project brief for a new software project. Use when starting a new project and need to define scope, goals, and constraints before speccing.
argument-hint: [project-slug]
allowed-tools: Read, Write, Glob
---

Write a project brief for `$0`.

## Steps

1. Check if `software-engineering/workflows/01-briefs/$0-brief.md` already exists — if so, read it and offer to update rather than overwrite
2. Read `software-engineering/PROJECTS.md` to understand context of existing projects
3. Read `software-engineering/docs/tech-standards.md` for stack constraints
4. Interview the user if needed — ask what the project does and who it's for before writing

## Brief Format

Create `software-engineering/workflows/01-briefs/$0-brief.md`:

```markdown
# [Project Name] — Brief

**Slug:** $0
**Track:** [job-search | freelance | solopreneur | agent-work]
**Status:** draft
**Date:** [YYYY-MM-DD]

## Problem

[1–3 sentences. What problem does this solve? Who has it?]

## Proposed Solution

[What the software does. Not how — just what.]

## Goals

- [Goal 1 — measurable if possible]
- [Goal 2]
- [Goal 3]

## Non-Goals (out of scope)

- [What this explicitly does NOT do]

## Users

[Who uses this? How technical are they? What's their context?]

## Constraints

- **Stack:** [from tech-standards.md — Python, C#, Blazor, etc.]
- **Platform:** [desktop | web | CLI | bot | API]
- **Timeline:** [rough sense — days, weeks, months]
- **Dependencies:** [other projects, APIs, services]

## Success Criteria

[How do you know when this is done and working?]

## Open Questions

- [ ] [Question 1]
- [ ] [Question 2]
```

## After writing

Say: "Brief written. Next step: `/develop-requirements $0` to turn this into a full spec, or `/plan-architecture $0` to think about structure first."

## Rules

- If the user hasn't told you enough to fill a section, write `[TBD — ask user]` rather than guessing
- Do not start a brief with generic boilerplate — lead with the actual problem
- Keep it short: a brief should fit on one screen
