---
name: plan-architecture
description: Design the system architecture for a software project. Use after a brief or spec exists, before build begins.
argument-hint: [project-slug]
allowed-tools: Read, Write, Glob
---

Design the architecture for `$0`.

## Steps

1. Read `software-engineering/workflows/01-briefs/$0-brief.md` (required)
2. Read `software-engineering/workflows/02-specs/$0-spec.md` if it exists
3. Read `software-engineering/docs/tech-standards.md`
4. Read `software-engineering/docs/architecture-patterns.md`
5. Check if a previous architecture doc exists at `software-engineering/workflows/02-specs/$0-architecture.md` — read it if so

## Output

Create or update `software-engineering/workflows/02-specs/$0-architecture.md`:

```markdown
# [Project Name] — Architecture

**Slug:** $0
**Date:** [YYYY-MM-DD]
**Status:** draft | approved

## System Overview

[1 paragraph: what the system does and how the major pieces fit together]

## Component Map

```
[mermaid or prose diagram of components and their relationships]
```

## Components

### [Component Name]
- **Responsibility:** [what it owns]
- **Technology:** [language, framework, library]
- **Interface:** [how other components call it]

### [Component Name]
- ...

## Data Flow

[How data moves through the system from input to output — numbered steps]

1. [User/input action]
2. [Component A receives and does X]
3. [Component B does Y with result]
4. [Output/storage]

## Storage

| Store | Type | What lives here |
| ----- | ---- | --------------- |
| [name] | file / sqlite / postgres / etc. | |

## External Dependencies

| Dependency | Purpose | Risk if unavailable |
| ---------- | ------- | ------------------- |
| [API/service] | | |

## Key Design Decisions

| Decision | Choice | Rationale |
| -------- | ------ | --------- |
| [e.g., sync vs async] | [choice] | [why] |

## Trade-offs and Risks

- **[Risk 1]:** [What could go wrong and mitigation]
- **[Risk 2]:** [...]

## What This Architecture Explicitly Does NOT Do

[Boundaries — helps future-you not scope-creep the design]
```

## After writing

Say: "Architecture documented. From here: `/design-api $0` for interface contracts, `/design-frontend $0` for UI flow, or start coding and use `/code-review $0` when ready for a review."

## Rules

- Prefer simple architectures — do not introduce layers that don't carry their weight
- Ground every component in the tech-standards.md stack unless there's a good reason to deviate
- Name the trade-offs explicitly — a design that pretends to have no downsides is incomplete
