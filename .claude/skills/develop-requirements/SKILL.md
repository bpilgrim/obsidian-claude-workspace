---
name: develop-requirements
description: Develop a requirements document (spec) from a brief. Use when a brief exists and the project is moving from idea to implementation-ready.
argument-hint: [project-slug]
allowed-tools: Read, Write, Glob
---

Develop a requirements spec for `$0`.

## Steps

1. Read `software-engineering/workflows/01-briefs/$0-brief.md` — if it doesn't exist, stop and say "Run `/write-brief $0` first"
2. Read `software-engineering/docs/tech-standards.md`
3. Read `software-engineering/docs/architecture-patterns.md` if it exists
4. Check if `software-engineering/workflows/02-specs/$0-spec.md` already exists — if so, read it and offer to update

## Spec Format

Create `software-engineering/workflows/02-specs/$0-spec.md`:

```markdown
# [Project Name] — Spec

**Slug:** $0
**Brief:** `workflows/01-briefs/$0-brief.md`
**Status:** draft | in-review | approved
**Date:** [YYYY-MM-DD]

## Functional Requirements

### [Feature Area 1]
- FR-01: [The system shall...]
- FR-02: [The system shall...]

### [Feature Area 2]
- FR-03: [...]

## Non-Functional Requirements

- NFR-01: Performance — [specific target]
- NFR-02: Security — [specific constraint]
- NFR-03: Reliability — [uptime, error handling expectation]

## Data Model

[Entities, fields, relationships — can be prose or table]

| Entity | Fields | Notes |
| ------ | ------ | ----- |
| [Name] | [field1, field2] | |

## User Flows

### [Flow Name]
1. [Step 1]
2. [Step 2]
3. [Step 3 — happy path]
- **Error path:** [what happens when it fails]

## API / Interface Contract

[If applicable — endpoints, inputs, outputs, error codes]

## Tech Stack

[Specific choices for this project, within standards from tech-standards.md]

- **Language:**
- **Framework:**
- **Storage:**
- **External dependencies:**

## Out of Scope

[Pulled from brief — anything explicitly excluded]

## Open Questions

- [ ] [Question requiring decision before build]

## Acceptance Criteria

- [ ] [Testable condition 1]
- [ ] [Testable condition 2]
```

## After writing

Review the brief to determine what to run next:

- Always suggest `/plan-architecture $0` for system design
- If the brief describes any user-facing UI (desktop app, web UI, Blazor pages, admin interface), run `/design-frontend $0` now — do not wait for the user to ask
- If the project has an API boundary (HTTP endpoints, bot commands, CLI, module interface), suggest `/design-api $0`

Say: "Spec written. Next: `/plan-architecture $0` for system design[, running `/design-frontend $0` now since this project has UI][, and `/design-api $0` for the API contract]."

## Rules

- Requirements should be testable — "the system shall display an error message" not "the system should handle errors"
- Keep data model lightweight — this isn't a DB schema, it's a concept map
- If you need a decision from the user, list it in Open Questions rather than guessing
