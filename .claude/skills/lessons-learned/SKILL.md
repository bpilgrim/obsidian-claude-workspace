---
name: lessons-learned
description: Capture lessons learned from a completed or shipped project. Use after a release or at project close to extract reusable insights.
argument-hint: [project-slug]
allowed-tools: Read, Write, Glob
---

Capture lessons learned from `$0`.

## Steps

1. Read `software-engineering/PROJECTS.md` — get project context and current status
2. Read the most recent release log in `software-engineering/workflows/03-builds/$0/release/`
3. Read `software-engineering/workflows/01-briefs/$0-brief.md` — compare original goals to what shipped
4. Read `software-engineering/workflows/02-specs/$0-spec.md` if it exists — note what changed from spec to ship
5. Ask the user: "What surprised you? What would you do differently? What worked well?"

## Output

Create `software-engineering/workflows/03-builds/$0/lessons-learned.md`:

```markdown
# [Project Name] — Lessons Learned

**Date:** [YYYY-MM-DD]
**Version reviewed:** [vX.Y.Z]

---

## What went well

- [Specific thing — be concrete, not "teamwork was good"]
- [Specific thing]

## What didn't go well

- [Specific problem — what happened, not just that it was bad]
- [Specific problem]

## What surprised me

- [Assumption that turned out to be wrong]
- [Thing that was harder or easier than expected]

## What I'd do differently

- [Specific change to approach, tools, process, or sequence]
- [Specific change]

## Insights to carry forward

- [Reusable principle — stated as a rule you'd apply to the next project]
- [Reusable principle]

## Things to watch on the next project like this

- [Risk that materialized here that might appear again]
- [Pattern to recognize early]

## Unresolved questions

- [ ] [Open question this project surfaced but didn't answer]
```

## After writing

Say: "Lessons captured. Consider adding key reusable principles to `software-engineering/docs/architecture-patterns.md` or the relevant knowledgebase topic."

## Rules

- Be specific — "I underestimated the complexity of the Telegram state machine" is useful; "scoping was hard" is not
- This is for your future self — write it as advice you'd give yourself at the start of the next similar project
- Don't just list problems — the "insights to carry forward" section is the most valuable part
- If the project is still active, still write it — partial lessons are better than none
