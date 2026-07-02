---
name: debug-issue
description: Debug a specific issue or error in a software project. Use when something is broken and the cause is not obvious.
argument-hint: [project-slug] [brief-description-of-issue]
allowed-tools: Read, Glob, Grep, Bash
---

Debug issue in `$0`: `$1`

## Steps

1. Read any error message or symptom the user has provided — understand exactly what's failing and when
2. Read `software-engineering/workflows/02-specs/$0-spec.md` to understand expected behavior
3. Locate the relevant source files using Glob or Grep — start with the component most likely involved
4. Read the source code around the failure point
5. Trace the execution path: where does the input come from, what transforms it, where does it fail?

## Debugging Approach

Work through these layers in order — stop when you find the cause:

**Layer 1 — Reproduce**
- What are the exact inputs that trigger the failure?
- Is it always reproducible or intermittent?
- What's the last known good state?

**Layer 2 — Isolate**
- Which component owns the failure?
- What is the component receiving as input?
- What is it producing (or failing to produce)?

**Layer 3 — Root cause**
- What assumption in the code is violated?
- Is it a logic error, a data error, a timing issue, or an integration failure?
- What changed recently that could have introduced this?

**Layer 4 — Fix**
- What's the minimal change that fixes the root cause?
- Does the fix introduce any new risk?
- Should a test be added to prevent regression?

## Output Format

```
## Debug Report — [issue description]

**Project:** $0
**Symptom:** [what fails, what error appears]
**Root Cause:** [the actual reason it's failing — specific, not vague]

### Trace

1. [Input received]
2. [Component A does X]
3. [Failure occurs here — file:line — because Y]

### Fix

[Specific change to make — be concrete. Include the before/after if code is short.]

### Regression Prevention

- [ ] Add test: [description of test case that would have caught this]

### Related Risks

- [Any adjacent code that might have the same issue]
```

## Rules

- Do not guess at root cause — trace the code path to find where the assumption breaks
- Minimal fix — fix the root cause, not the symptom
- If you can't reproduce or trace the issue from code alone, say so and ask the user for more information (logs, exact input, steps to reproduce)
- Always suggest a regression test unless the bug is environmental (config, infra) not code
