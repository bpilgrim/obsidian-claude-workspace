---
name: write-readme
description: Write a README for a software project. Use when a project is ready to be shared, published, or handed off.
argument-hint: [project-slug]
allowed-tools: Read, Write, Glob, Grep
---

Write a README for `$0`.

## Steps

1. Read `software-engineering/workflows/01-briefs/$0-brief.md`
2. Read `software-engineering/workflows/02-specs/$0-spec.md` if it exists
3. Read `software-engineering/docs/tech-standards.md` for stack
4. Glob the project source directory to understand actual structure
5. Check if a README already exists — if so, read it and update rather than replace

## Output

Write to the project's source root (ask user for path if unknown, or default to `software-engineering/[category]/$0/README.md`):

```markdown
# [Project Name]

[One sentence: what this does and who it's for]

## What it does

[2–4 sentences expanding on the one-liner. What problem does it solve? What's the core behavior?]

## Quick start

### Prerequisites

- [Runtime/version]
- [Dependencies]

### Install

```bash
[install commands]
```

### Run

```bash
[run command]
```

[Screenshot or example output here if helpful]

## Configuration

| Variable / Setting | Default | Description |
| ------------------ | ------- | ----------- |
| [VAR_NAME] | [value] | [what it controls] |

## Usage

[Key use cases with examples. More than quick start but not exhaustive.]

```[language]
[code example]
```

## Project structure

```
[project-root]/
├── [file/dir]     # [what it does]
└── [file/dir]     # [what it does]
```

## Development

```bash
# Run tests
[test command]

# Lint / format
[lint command]
```

## Status

[Active development | Stable | Maintained | Archived]

[Link to PROJECTS.md entry if relevant]
```

## After writing

Say: "README written. Run `/log-release $0` to document the first release, or push the repo to make it public."

## Rules

- Write for someone who hasn't seen the code — assume they need to install and run it from scratch
- Quick start must actually work — test the commands mentally against what the code does
- Keep it honest about project status — don't oversell completeness
- Omit sections that don't apply (e.g., no Configuration section if there's nothing to configure)
