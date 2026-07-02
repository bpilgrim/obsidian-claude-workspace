# obsidian-claude-workspace — Setup Guide

A structured workspace system for Obsidian + Claude Code. Organizes your life into focused areas, each with its own AI instructions.

---

## Prerequisites

- [Obsidian](https://obsidian.md) — this is another interface into the folder structure where you will store your data
- [Claude Code](https://claude.ai/code) — point it at this folder structure
- Dataview plugin (Obsidian) — use for dashboard views (optional)

---

## Quick Start

**1. Clone the repo**
```bash
git clone [your-repo-url] my-workspace
cd my-workspace
```

**2. Open as an Obsidian vault**
In Obsidian: Open folder as vault → select this folder.

**3. Point Claude Code at it**
```bash
cd my-workspace
claude
```

**4. Let the AI guide you through setup**

Say: *"I just set up this workspace. Help me customize it."*

The AI will read `CONTEXT.md` and walk you through:
- Choosing your life-area folders
- Setting up your work tracks
- Filling in your tech stack (if you're a developer)

---

## What's Included

| Path | What it is |
| ---- | ---------- |
| `CLAUDE.md` | Always-in-context map — folder structure and naming conventions |
| `CONTEXT.md` | Root-level onboarding and routing |
| `software-engineering/` | Full pipeline for software projects: briefs → specs → builds → releases |
| `personal-productivity/` | Tasks, projects, and work tracks |
| `_INTERNAL/_inbox/` | Capture anything unrouted here |
| `.claude/skills/` | Slash-command workflows |

---

## Key Skills (slash commands)

**Software engineering:**
- `/write-brief [slug]` — start a new project
- `/develop-requirements [slug]` — write a spec
- `/plan-architecture [slug]` — design the system
- `/design-frontend [slug]` — UI flows and components
- `/code-review [slug]` — review code against spec
- `/log-release [slug] [version]` — record a release

**Knowledge:**
- `/distill-source` — extract key ideas from an article or resource
- `/study-topic [topic]` — deep dive on a subject
- `/quiz-me [topic]` — test your knowledge

---

## Customization Checklist

- [ ] Add your life-area folders (household, journal, vocation, etc.) with `CONTEXT.md` in each
- [ ] Update `CLAUDE.md` folder structure and quick navigation table
- [ ] Define your work tracks in `personal-productivity/2_projects/tracks/`
- [ ] Identify your recurring workflows and systematize them (see below)
- [ ] Fill in `software-engineering/docs/tech-standards.md` with your stack
- [ ] Remove skills you won't use from `.claude/skills/`

---

## Systematizing Your Workflows

The highest-leverage thing you can do in this system is give your recurring multi-step work a structured home — the way `software-engineering/` gives code projects a pipeline.

**A workflow worth systematizing** happens repeatedly, has discrete stages, produces artifacts, and benefits from AI help.

To set one up, tell the AI: *"I want to systematize my [workflow]. Here's how it works: [describe your steps]."*

The AI will design:
- A folder structure for the workflow's artifacts
- A `CONTEXT.md` with stage definitions and agent instructions
- Templates for recurring documents
- Optionally, skills (slash commands) for the most AI-assisted stages

**Reference:** `software-engineering/CONTEXT.md` is the best example of a fully-systematized workflow in this repo. Study it to understand what a mature pipeline looks like.

---

## How It Works

Each folder has a `CONTEXT.md` that tells the AI what lives there and how to work with it. The AI reads the relevant `CONTEXT.md` before acting — no prompting required.

```
CLAUDE.md       always loaded — the map
CONTEXT.md      per-folder instructions
Skills          reusable workflows invoked with /slash-commands
```

See `CONTEXT.md` (root) for the full first-time setup walkthrough.

Want to understand *why* the system works the way it does? Read `TUTORIAL.md`.
