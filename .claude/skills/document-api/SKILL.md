---
name: document-api
description: Generate public-facing API documentation from the API design and source code. Use when an API is stable enough to document for consumers.
argument-hint: [project-slug]
allowed-tools: Read, Write, Glob, Grep
---

Generate API documentation for `$0`.

## Steps

1. Read `software-engineering/workflows/03-builds/$0/api-design.md` — primary source of truth
2. Read the actual source files to confirm current implementation matches the design doc
3. Read `software-engineering/workflows/02-specs/$0-spec.md` for context on purpose and constraints
4. Note any gaps between the design doc and the implementation — flag them

## Output

Create `software-engineering/workflows/03-builds/$0/api-docs.md`:

```markdown
# [Project Name] — API Reference

**Version:** [from PROJECTS.md or release log]
**Base:** [base URL, module path, or command prefix]
**Auth:** [method]
**Date:** [YYYY-MM-DD]

---

## Overview

[2–3 sentences: what this API does, who it's for, what it enables]

## Quick Start

```[language]
# Minimal working example
[code snippet showing the simplest useful call]
```

---

## [Resource / Module / Command Group]

### [Endpoint / Function / Command]

**`[METHOD /path]`** or **`def fn(args) -> ReturnType`** or **`/command [args]`**

[One sentence: what this does]

**Parameters / Arguments:**

| Name | Type | Required | Description |
| ---- | ---- | -------- | ----------- |
| [param] | [type] | Yes/No | [description] |

**Example Request:**
```[language]
[complete working example]
```

**Example Response:**
```json
{
  "field": "value"
}
```

**Errors:**

| Code / Exception | When it occurs |
| ---------------- | -------------- |
| [code] | [condition] |

---

## Error Reference

| Code | Meaning | Common cause |
| ---- | ------- | ------------ |
| [code] | [name] | [when it happens] |

## Changelog

| Version | Change |
| ------- | ------ |
| [v0.1] | Initial release |
```

## After writing

Say: "API docs written at `software-engineering/workflows/03-builds/$0/api-docs.md`. If you're ready to ship, run `/log-release $0` next."

## Rules

- Document the API as it actually exists in code — if design and code differ, note the discrepancy and ask which is correct
- Every endpoint/function needs at least one complete, working example
- Write for the consumer, not the implementer — omit internal implementation details
