<!--
===============================================================
TEACHING NOTE: This is LAYER 1 - THE MAP.

CLAUDE.md is auto-loaded into every conversation. It's always in context.
That makes it prime real estate. Use it for:

1. Folder structure (so the agent always knows where things live)
2. ID systems & naming conventions (so files land in the right place)
3. File placement rules (so nothing gets lost)
4. Quick navigation table (task -> workspace)

Do NOT put:
    - Detailed instructions (those go in workspace CONTEXT.md files)
    - Voice/style guides (those go in your personal notes)
    - Pipeline details (those go in workflows/CONTEXT.md)

Keep it under 200 lines. Every line here costs tokens in EVERY conversation.

SETUP NOTE: Replace all [placeholder] values with your own content.
The root CONTEXT.md will guide you through customization.
===============================================================
-->

## Standing Rules

**Never read files ending in `-private.md`.** These contain sensitive identifiers (account numbers, policy numbers, VINs, member IDs). If a task requires one of these values, ask the user to provide it directly in the conversation.

---

## What This Is

A workspace system for an individual's work and personal life. Captures and organizes various life areas, interests, projects, thoughts, and artifacts. An agent drops into a workspace folder, reads its CONTEXT.md, does its work, and exits.

**CONTEXT.md** (top-level) routes you to the right workspace. This file is the map.

---

## Folder Structure

```
[vault-root]/
├── CLAUDE.md
├── CONTEXT.md
│
├── _INFO/
├── _INTERNAL/
│    ├── _inbox/
│    ├── archive/
│    └── attachments/
│
├── software-engineering/        ← code projects, specs, builds
│    ├── CONTEXT.md
│    ├── PROJECTS.md
│    ├── docs/
│    └── workflows/
│         ├── 01-briefs/
│         ├── 02-specs/
│         └── 03-builds/
│
├── personal-productivity/       ← goals, projects, tasks, dashboard
│    ├── CONTEXT.md
│    ├── 1_goals/
│    ├── 2_projects/
│    │    └── tracks/
│    └── 3_tasks/
│
│   [Add your own life-area folders below]
│   Examples: household/, journal/, knowledgebase/, vocation/, health/
│   Each needs a CONTEXT.md — see root CONTEXT.md for guidance
│
└── [your-life-area]/
     └── CONTEXT.md
```

---

## Quick Navigation

| Want to...                              | Go here                              |
| --------------------------------------- | ------------------------------------ |
| Plan my week / what to work on          | `personal-productivity/CONTEXT.md`   |
| Track a work project                    | `personal-productivity/2_projects/`  |
| Log a task                              | `personal-productivity/3_tasks/`     |
| Code projects and technical work        | `software-engineering/`              |
| Unrouted captures                       | `_INTERNAL/_inbox/`                  |
| [Add your own rows as you build out]    |                                      |

---

## ID & Naming Conventions

| Content Type        | Pattern                        | Example                          |
| ------------------- | ------------------------------ | -------------------------------- |
| Build specs         | `[slug]-spec.md`               | `auth-demo-spec.md`              |
| Journal entry       | `[YYYY-MM-DD]-[slug].md`       | `2026-03-10-launch-week.md`      |
| Task file           | `[slug]-[8-char-id].md`        | `update-resume-cf822801.md`      |
| Work track file     | `track-[name].md`              | `track-job-search.md`            |
| SW project stub     | `[slug].md` (in 2_projects/)   | `ai-assistant.md`                |
| Non-SW project dir  | `[slug]/` (in 2_projects/)     | `my-project/`                    |
| Project README      | `README.md` (in project dir)   | `my-project/README.md`           |
| SW brief            | `[slug]-brief.md`              | `my-app-brief.md`                |
| SW brief (feature)  | `[project]-[feature]-brief.md` | `my-app-auth-brief.md`           |
| SW spec             | same pattern as brief, `-spec.md` | `my-app-spec.md`              |
| SW build notes      | same pattern as brief, `-notes.md` | `my-app-notes.md`            |
| SW release folder   | `release/[project]/v[version]/` | `release/my-app/v1.0/`          |
