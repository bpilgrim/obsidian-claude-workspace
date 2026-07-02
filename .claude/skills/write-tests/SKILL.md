---
name: write-tests
description: Write tests for a software project or specific component. Use after a spec exists and code is written or being written.
argument-hint: [project-slug] [component-or-file]
allowed-tools: Read, Write, Glob, Grep
---

Write tests for `$0` — specifically `$1`.

## Steps

1. Read `software-engineering/workflows/02-specs/$0-spec.md` — acceptance criteria become test cases
2. Read `software-engineering/docs/tech-standards.md` — determines test framework (pytest for Python, xUnit/NUnit for C#, etc.)
3. Read the source file(s) being tested: `$1`
4. Check if tests already exist (look for `tests/`, `test_*.py`, `*Tests.cs`, etc.) — if so, extend rather than replace

## Test Strategy

Determine what type of tests to write based on what's being tested:

- **Unit tests** — pure functions, isolated components, data transformations
- **Integration tests** — components that talk to each other, file I/O, DB queries
- **Contract tests** — API endpoints, external integrations
- **Behavior tests** — user flows end-to-end

## Coverage Targets

For each function or component, write tests covering:

1. **Happy path** — expected input, expected output
2. **Edge cases** — empty, null, zero, max-length, boundary values
3. **Error paths** — invalid input, missing dependencies, failure conditions
4. **State transitions** — if the component is stateful, test each transition

## Output

Write test file(s) appropriate to the stack. Name them following project conventions or:
- Python: `test_[module].py`
- C#: `[Class]Tests.cs`

Each test should:
- Have a clear name describing what it tests (`test_extracts_title_from_empty_message`)
- Arrange inputs, Act (call the thing), Assert the result — AAA pattern
- Be independent — no test should depend on another test's side effects

## After writing

Present a summary:
```
## Tests Written

**File:** [path]
**Tests:** [N] tests across [N] functions/components

| Test | Type | What it covers |
| ---- | ---- | -------------- |
| [test_name] | unit | [what it verifies] |

**Not covered:**
- [Thing left untested and why — external API, not yet implemented, etc.]

**To run:**
[command to execute the test suite]
```

## Rules

- Write tests in the language and framework the project actually uses
- Do not mock what you can test directly — prefer real behavior over mocked behavior for integration tests
- If the code is too tightly coupled to test, note it as a finding rather than writing bad tests
- Tests should fail for the right reason — a test that always passes is worse than no test
