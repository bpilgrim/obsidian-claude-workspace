---
name: design-frontend
description: Design the frontend — screens, flows, and component structure — for a software project. Use before building UI.
argument-hint: [project-slug]
allowed-tools: Read, Write, Glob
---

Design the frontend for `$0`.

## Steps

1. Read `software-engineering/workflows/02-specs/$0-spec.md` — if it doesn't exist, read the brief
2. Read `software-engineering/docs/tech-standards.md` for UI stack (Blazor, WPF, web, etc.)
3. Read any existing architecture doc at `software-engineering/workflows/02-specs/$0-architecture.md`

## Output

Create `software-engineering/workflows/02-specs/$0-frontend-design.md`:

```markdown
# [Project Name] — Frontend Design

**Slug:** $0
**Date:** [YYYY-MM-DD]
**Stack:** [Blazor | WPF | HTML/CSS/JS | other]

## Screens / Views

### [Screen Name]
- **Route / trigger:** [URL or navigation action]
- **Purpose:** [what the user accomplishes here]
- **Key elements:**
  - [Element 1 — label, input, button, list, etc.]
  - [Element 2]
- **Actions:** [what the user can do — and what happens]
- **Error states:** [what shows when something fails]

### [Screen Name]
- ...

## Navigation / Flow

```
[Screen A] → [action] → [Screen B]
[Screen A] → [error] → [Error State]
```

## Component Breakdown

| Component | Reused on | Inputs | Behavior |
| --------- | --------- | ------ | -------- |
| [Name] | [screens] | [props/data] | [what it does] |

## State Management

[Where does UI state live? What triggers re-renders or reloads?]

## Loading and Empty States

| Screen | Loading behavior | Empty state message |
| ------ | ---------------- | ------------------- |
| [Name] | [spinner / skeleton / none] | [what to show when no data] |

## Accessibility Notes

- [Key a11y considerations — keyboard nav, screen reader labels, contrast]

## Open Design Questions

- [ ] [Decision needed before build]
```

## After writing

Say: "Frontend design documented. Next: `/design-api $0` if there's a backend to wire up, or start building and use `/code-review $0` for a review pass."

## Rules

- Design for the actual stack in tech-standards.md — don't design a React app if the project uses Blazor
- Name error states and empty states explicitly — these are often skipped and cause poor UX
- Keep component breakdown lightweight — this isn't a component library, it's a design reference
