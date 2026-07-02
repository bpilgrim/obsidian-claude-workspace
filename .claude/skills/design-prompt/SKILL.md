---
name: design-prompt
description: Design and document the prompt architecture for an AI-powered feature or agent. Use when a project uses Claude or any LLM and needs deliberate prompt engineering.
argument-hint: [project-slug] [feature-or-component-name]
allowed-tools: Read, Write, Glob
---

Design the prompt architecture for `$0` — specifically for `$1`.

## Steps

1. Read `software-engineering/workflows/02-specs/$0-spec.md`
2. Read `software-engineering/workflows/03-builds/$0/architecture.md` if it exists
3. Read `software-engineering/docs/tech-standards.md` — note the default model (claude-sonnet-4-6)
4. Understand: what decision or generation is the LLM being asked to make? What does it need to know?

## Output

Create `software-engineering/workflows/03-builds/$0/prompt-design-$1.md`:

```markdown
# [Project Name] — Prompt Design: [Feature/Component]

**Slug:** $0
**Component:** $1
**Model:** claude-sonnet-4-6 (or specify override)
**Date:** [YYYY-MM-DD]

## What the LLM is doing

[One paragraph: the specific task the model performs, the decision it makes, or the content it generates]

## Inputs to the prompt

| Variable | Source | Description |
| -------- | ------ | ----------- |
| [var_name] | [user input / file / DB / prior turn] | [what it contains] |

## Prompt Structure

### System Prompt

```
[Full system prompt text]
```

**Design notes:**
- [Why this framing / persona / constraint]
- [What the system prompt is responsible for vs. what goes in the user turn]

### User Turn Template

```
[Template with {variable} placeholders]
```

### Assistant Primer (if used)

```
[Pre-fill text for the assistant turn, if applicable]
```

## Output Format

- **Format:** [prose | JSON | markdown | structured list]
- **Schema (if JSON):**
```json
{
  "field": "type and description"
}
```
- **Parsing:** [how the output is consumed — regex, json.loads, direct display]

## Context Window Budget

| Section | Estimated tokens |
| ------- | ---------------- |
| System prompt | ~[N] |
| User content | ~[N] |
| Expected output | ~[N] |
| **Total** | ~[N] |

## Failure Modes

| Failure | How to detect | Mitigation |
| ------- | ------------- | ---------- |
| [Hallucination risk] | [check] | [guard] |
| [Format failure] | [check] | [retry / fallback] |
| [Off-task response] | [check] | [retry / fallback] |

## Test Cases

| Input | Expected output behavior |
| ----- | ------------------------ |
| [example] | [what good looks like] |
| [edge case] | [what should happen] |

## Iteration Log

| Date | Change | Reason |
| ---- | ------ | ------ |
| [YYYY-MM-DD] | [what changed] | [why] |
```

## After writing

Say: "Prompt design documented. Use `/design-agent $0` if this is part of an agent system, or start implementing and iterate using the test cases above."

## Rules

- Document the actual prompt text, not a description of it — the file should be runnable reference
- Every prompt design needs at least 2 test cases: happy path and one edge/failure case
- Track the iteration log from the start — prompt engineering is iterative and the history matters
- Note token budget early — context limits are a real constraint, especially with large inputs
