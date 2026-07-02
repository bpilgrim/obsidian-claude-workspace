---
name: design-api
description: Design the API contract for a software project — endpoints, inputs, outputs, and error codes. Use before building any interface that crosses a boundary (HTTP, bot, CLI, module).
argument-hint: [project-slug]
allowed-tools: Read, Write, Glob
---

Design the API for `$0`.

## Steps

1. Read `software-engineering/workflows/02-specs/$0-spec.md`
2. Read `software-engineering/docs/tech-standards.md`
3. Read `software-engineering/workflows/02-specs/$0-architecture.md` if it exists
4. Determine API style from the project context: REST, Python module API, Telegram bot commands, CLI interface, or internal function contracts

## Output

Create `software-engineering/workflows/02-specs/$0-api-design.md`:

```markdown
# [Project Name] — API Design

**Slug:** $0
**Date:** [YYYY-MM-DD]
**Style:** [REST | module | bot-commands | CLI | internal]

## Base

[Base URL, module path, or command prefix]

## Authentication

[API key | session token | none | Telegram user_id | other]

---

## Endpoints / Commands / Functions

### [Endpoint or function name]

**Method / Trigger:** `[GET | POST | PUT | DELETE | /command | function_name()]`
**Path / Signature:** `[/path or def fn(arg1, arg2) -> ReturnType]`
**Purpose:** [one sentence]

**Input:**
```json
{
  "field": "type — description"
}
```

**Success Response:**
```json
{
  "field": "value"
}
```

**Error Responses:**
| Code / Exception | Condition |
| ---------------- | --------- |
| 400 / ValueError | [when] |
| 404 / KeyError   | [when] |
| 500 / Exception  | [when] |

**Notes:** [edge cases, rate limits, side effects]

---

## Shared Types / Models

```
[TypeName]
  field: type — description
  field: type — description
```

## Versioning

[How breaking changes will be handled, if relevant]

## Rate Limits / Quotas

[Any limits the caller needs to know about]
```

## After writing

Say: "API design documented. Next: `/write-tests $0` to spec the test cases from this contract, or `/document-api $0` to generate the public-facing docs."

## Rules

- Design for the actual transport — don't write REST docs for a Python module, don't write function signatures for a Telegram bot
- Every endpoint needs at least one error case defined
- If the API is internal-only (module imports, not HTTP), document the function signatures and return types
