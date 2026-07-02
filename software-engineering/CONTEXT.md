# software-engineering

This workspace holds the planning, specification, and documentation artifacts for all software projects. Source code lives in git repositories outside the vault — this workspace holds the **thinking layer** around that code.

---

## What Lives Here

| Path | Contents |
| ---- | -------- |
| `PROJECTS.md` | Registry of all software projects — category, track, pipeline stage, repo path |
| `docs/tech-standards.md` | Languages, frameworks, versions, and conventions used across projects |
| `docs/architecture-patterns.md` | Patterns and approaches used repeatedly — reference before designing |
| `docs/dev-environment.md` | Tools, configs, accounts, environment setup |
| `docs/project-setup.md` | Standard checklist for starting a new project — gitignore, structure, config pattern |
| `workflows/01-briefs/` | `[slug]-brief.md` — what to build, why, success criteria *(active projects only)* |
| `workflows/02-specs/` | `[slug]-spec.md` — technical design, architecture, approach *(active projects only)* |
| `workflows/03-builds/` | `[slug]-notes.md` — dev journal, decisions log, blockers *(active projects only)* |
| `release/[project]/v[version]/` | All artifacts for a shipped version — brief, spec, build notes, release log |
| `release/[project]/v[version]/features/[feature-slug]/` | Feature artifacts for features shipped in that version — brief, spec, build notes |

---

## The Pipeline

Every project moves through these stages:

```
01-briefs  →  02-specs  →  03-builds  →  release/[project]/v[version]/
(what)         (how)        (doing)                (done)
```

Not every project needs every stage. A small utility might go brief → build. A product needs all four.

**On release:** all workflow artifacts (brief, spec, build notes) are moved from the active folders into `release/[project]/v[version]/` alongside the release log. The active workflow folders only contain in-progress work.

**Feature work on an existing project** follows the same pipeline with a compound slug: `[project]-[feature]`. Example: `ai-assistant-v2-triage-improvements-brief.md`. On release, these move into `release/ai-assistant-v2/v1.1/`.

## Naming Conventions

| Artifact | Active location | Filename pattern | Example |
| -------- | --------------- | ---------------- | ------- |
| Brief (new project) | `workflows/01-briefs/` | `[slug]-brief.md` | `ai-assistant-v2-brief.md` |
| Brief (feature) | `workflows/01-briefs/` | `[project]-[feature]-brief.md` | `ai-assistant-v2-triage-improvements-brief.md` |
| Spec | `workflows/02-specs/` | same pattern as brief | `ai-assistant-v2-spec.md` |
| Build notes | `workflows/03-builds/` | same pattern, `-notes.md` | `ai-assistant-v2-notes.md` |
| Release log | `release/[project]/v[version]/` | `release-log.md` | `release/ai-assistant-v2/v1.0/release-log.md` |
| Feature brief | `release/[project]/v[version]/features/[feature-slug]/` | `brief.md` | `release/ai-assistant-v2/v1.1/features/task-completion/brief.md` |
| Feature spec | same feature folder | `spec.md` | — |
| Feature build notes | same feature folder | `build-notes.md` | — |

---

## Project Categories

| Category | Description |
| -------- | ----------- |
| `ai-infrastructure` | Personal AI system — assistant, bot, tools |
| `products` | Solopreneur products and services |
| `freelance-software` | Client work |
| `writing` | Writing tools and utilities |

Categories are organizational labels tracked in `PROJECTS.md`, not physical subfolders.

---

## Agent Instructions

### "Start a new project"
1. Add a row to `PROJECTS.md` with category, track, stage = `brief`
2. Create `workflows/01-briefs/[slug]-brief.md`
3. If project has a personal-productivity stub, link it in the PM Stub column
4. Read `docs/tech-standards.md` before making technology choices

### "What projects are in progress?"
1. Read `PROJECTS.md`
2. Filter rows where stage = `brief`, `spec`, or `build`
3. Return project name, stage, and track

### "Write a spec for [project]"
1. Read `workflows/01-briefs/[slug]-brief.md`
2. Read `docs/tech-standards.md` and `docs/architecture-patterns.md`
3. Create `workflows/02-specs/[slug]-spec.md`
4. Update stage in `PROJECTS.md` to `spec`

### During any coding work on a software project

These rules apply unconditionally whenever code is being written — no trigger phrase needed.

1. **At the start of a session:** read `workflows/03-builds/[slug]-notes.md` for context. If the file doesn't exist, create it before writing any code.
2. **Before starting the next phase:** write the current phase's notes. Do not begin the next layer (e.g., adapters, services, bot wiring) until the previous layer's notes are written.
3. **What to log:** what was built, key decisions and *why*, deviations from the spec, gotchas hit. Not a summary of code that can be read directly.
4. **Granularity:** one entry per coherent phase (domain layer done, adapters done, services done, etc.) — not after every file, not only at the very end.

### "Log a release for [project] version [version]"
1. Read `workflows/03-builds/[slug]-notes.md` for context
2. Create `release/[project]/v[version]/` folder
3. Write `release/[project]/v[version]/release-log.md`
4. Move `workflows/01-briefs/[slug]-brief.md` → `release/[project]/v[version]/brief.md`
5. Move `workflows/02-specs/[slug]-spec.md` → `release/[project]/v[version]/spec.md`
6. Move `workflows/03-builds/[slug]-notes.md` → `release/[project]/v[version]/build-notes.md`
7. For each feature shipped in this version, move feature artifacts into `release/[project]/v[version]/features/[feature-slug]/`:
   - `workflows/01-briefs/[project]-[feature]-brief.md` → `features/[feature-slug]/brief.md`
   - `workflows/02-specs/[project]-[feature]-spec.md` → `features/[feature-slug]/spec.md`
   - `workflows/02-specs/[project]-[feature]-architecture.md` → `features/[feature-slug]/architecture.md` (if exists)
   - `workflows/03-builds/[project]-[feature]-notes.md` → `features/[feature-slug]/build-notes.md`
8. Update stage in `PROJECTS.md` to `released`

### "Add a feature to [project]"
1. Create `workflows/01-briefs/[project]-[feature]-brief.md`
2. Add a row to `PROJECTS.md` or update the existing project row with the new feature scope
3. Follow the normal pipeline — spec, build, release
4. On release, feature artifacts move to `release/[project]/v[version]/`

### "What's the status of [project]?"
1. Read `PROJECTS.md` row for the project
2. Read the file in the current stage folder
3. If stage is `build`, also check if there's a PM stub in `personal-productivity/`

---

## Skills

| Skill | Invoke | Phase | When to use |
| ----- | ------ | ----- | ----------- |
| `write-brief` | `/write-brief [slug]` | Planning | Starting a new project — define scope and goals |
| `develop-requirements` | `/develop-requirements [slug]` | Planning | Turn a brief into a testable spec |
| `plan-architecture` | `/plan-architecture [slug]` | Planning | Design system structure before building |
| `design-frontend` | `/design-frontend [slug]` | Design | Screen flows, components, and UI states |
| `design-api` | `/design-api [slug]` | Design | API contracts, endpoints, function signatures |
| `design-prompt` | `/design-prompt [slug] [component]` | Design | Prompt engineering for AI-powered features |
| `code-review` | `/code-review [slug] [file]` | Build | Review code against spec before shipping |
| `write-tests` | `/write-tests [slug] [component]` | Build | Write test cases from spec and source code |
| `debug-issue` | `/debug-issue [slug] [issue]` | Build | Trace and fix a broken behavior |
| `document-api` | `/document-api [slug]` | Documentation | Public-facing API reference from design + code |
| `write-readme` | `/write-readme [slug]` | Documentation | README for sharing or publishing |
| `log-release` | `/log-release [slug] [version]` | Delivery | Record what shipped, known issues, what's next |
| `lessons-learned` | `/lessons-learned [slug]` | Delivery | Extract reusable insights after a release |
| `design-agent` | `/design-agent [slug] [agent]` | AI-specific | Agent tools, memory, decision flow, failure modes |

---

## Inbox Routing (for bot classification)

Route to `software-engineering/` when message contains:
- "new project", "build", "spec", "architecture", "tech stack"
- Project names listed in `PROJECTS.md`
- "repo", "codebase", "API", "deploy", "release", "version"
