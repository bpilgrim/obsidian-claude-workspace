---
name: code-review
description: Review code for correctness, quality, and alignment with project spec and tech standards. Use when code is ready for a review pass before shipping.
argument-hint: [project-slug] [file-or-path-to-review]
allowed-tools: Read, Glob, Grep
---

Review the code for `$0` at `$1`.

## Steps

1. Read `software-engineering/docs/tech-standards.md` — understand stack and conventions
2. Read `software-engineering/workflows/02-specs/$0-spec.md` if it exists — acceptance criteria are the correctness standard
3. Read the target file(s): `$1`
4. If `$1` is a directory or not specific, use Glob to find relevant source files
5. Read related files that the code interacts with (imports, callers, tests if they exist)

## Review Dimensions

Evaluate each dimension and produce findings:

### 1. Correctness
- Does the code do what the spec says it should?
- Are edge cases handled (empty input, null, error states)?
- Are there off-by-one errors, unhandled exceptions, or logic gaps?

### 2. Security
- Input validation at system boundaries (user input, external APIs)
- No hardcoded secrets or credentials
- No injection vulnerabilities (SQL, command, path traversal)
- No unsafe use of eval, exec, or dynamic code execution

### 3. Readability
- Are functions and variables named clearly?
- Is the logic followable without comments?
- Are comments present where logic is non-obvious?

### 4. Simplicity
- Is there unnecessary complexity?
- Could any section be simplified without losing correctness?
- Are there premature abstractions or over-engineered patterns?

### 5. Tech Standards Alignment
- Is the code using the approved stack?
- Does it follow conventions established in the codebase?

## Output Format

Present findings as:

```
## Code Review — [file or component]

### Summary
[1–2 sentence overall assessment: ship-ready / needs minor fixes / needs significant rework]

### Findings

**[CRITICAL | MAJOR | MINOR | NIT]** `[file:line]`
[Description of the issue]
[Suggested fix or direction]

...

### What's Working Well
- [Specific thing done well — be concrete]

### Recommended Next Steps
- [ ] [Fix 1]
- [ ] [Fix 2]
```

**Severity guide:**
- CRITICAL — incorrect behavior, security issue, data loss risk
- MAJOR — meaningful quality or correctness problem that should be fixed before ship
- MINOR — improvement that would meaningfully help maintainability or clarity
- NIT — style or preference, take or leave

## Rules

- Ground every finding in the code — cite file and line number
- Don't invent requirements not in the spec — review against what was agreed, not an imagined ideal
- Call out what's working well, not just problems
- If you can't read the spec (it doesn't exist), review against general correctness and say so
