# Workspace

This is the root of your obsidian-claude-workspace. Use this file to route to the right workspace, or to set it up for the first time.

---

## Is this a fresh workspace?

If `CLAUDE.md` still contains `[placeholder]` text, or your personal life-area folders don't exist yet, you're in setup mode. Follow the **First-Time Setup** section below.

If the workspace is already customized, skip to **Workspaces**.

---

## First-Time Setup

Run through these steps once. You don't need to do them all in one session.

### Step 1 — Decide on your life areas

Think about the distinct domains of your life that generate work, notes, or artifacts. Common examples:

| Life area | What lives there |
| --------- | ---------------- |
| `household/` | Home, finances, vehicles, family members, documents |
| `journal/` | Personal reflection, dreams, thoughts |
| `knowledgebase/` | Notes on topics you're learning, sources, references |
| `vocation/` | Resume, cover letters, job search, freelance work |
| `health/` | Medical, fitness, habits |

You don't need all of these. Add only what you'll actually use. You can always add more later.

### Step 2 — Create each life-area folder

For each life area you want, create a folder with a `CONTEXT.md` inside it. The `CONTEXT.md` should explain:
- What lives in this folder
- How it's organized (subfolders, file naming)
- Agent instructions — what the AI should do when asked questions about this area

**Ask the AI to help you write the CONTEXT.md** for any area you're unsure about. Describe what you want to track and it will draft one.

### Step 3 — Update CLAUDE.md

Once your folders exist, update the two sections in `CLAUDE.md`:
1. **Folder Structure** — add your life-area folders to the tree
2. **Quick Navigation** — add rows for each new area ("Want to... | Go here")

### Step 4 — Set up personal-productivity

`personal-productivity/` tracks what you're working on across all life areas. Open `personal-productivity/CONTEXT.md` and:
- Define your **work tracks** — the strategic lanes of your life (e.g. job search, freelance, side project, learning)
- Each track gets a file in `2_projects/tracks/track-[name].md`

The AI can help you define tracks if you describe your situation.

### Step 5 — Identify and systematize your workflows

The most powerful thing this system can do is give recurring multi-step work a structured home — the way `software-engineering/` gives code projects a pipeline from brief → spec → build → release.

**A workflow worth systematizing:**
- Happens repeatedly (not a one-off)
- Has discrete stages with clear inputs and outputs at each stage
- Produces artifacts that need to be organized and retrieved later
- Would benefit from AI assistance at one or more stages

**Ask yourself:** what do you do over and over that has multiple steps?

Common examples:

| Workflow | Stages | Lives in |
| -------- | ------ | -------- |
| Job search | posting → qualify → analyze → apply → prep → interview | `vocation/job-search/` |
| Freelance delivery | lead → proposal → project → delivery → invoice | `vocation/freelance-work/` |
| Knowledge capture | source → distill → notes → review | `knowledgebase/` |
| Content creation | idea → outline → draft → edit → publish | `content/` |
| Client onboarding | inquiry → scoping → contract → kickoff | `clients/` |

**For each workflow you identify:**

1. **Create a folder** inside the relevant life-area workspace (or as its own workspace if it's large)
2. **Write a CONTEXT.md** that describes:
   - The stages in order
   - What artifact lives at each stage and where
   - Agent instructions for each stage ("When I say 'analyze this posting', do X")
3. **Create templates** for recurring artifacts (e.g. a proposal template, a job analysis template)
4. **Write a skill** for any stage where the AI does significant work — this turns it into a slash command you can invoke anywhere

**Ask the AI to help design the workflow.** Describe what you do step by step and it will draft the CONTEXT.md, folder structure, and agent instructions. Use `software-engineering/CONTEXT.md` as a reference for how a well-structured workflow looks.

### Step 6 — Configure your tech stack (developers only)

If you do software development, open `software-engineering/docs/tech-standards.md` and fill in your languages, frameworks, and conventions. This file is read before any technical decision is made.

### Step 7 — Try a skill

The `.claude/skills/` directory contains reusable workflows. To start your first project:
```
/write-brief [your-project-name]
```
This kicks off the software engineering pipeline: brief → spec → architecture → build.

Or describe a workflow you want to set up and the AI will help you design it from scratch.

---

## Workspaces

Once set up, this table routes you to the right place:

| Area | Folder |
| ---- | ------ |
| Software projects | `software-engineering/` |
| Tasks and projects | `personal-productivity/` |
| Unrouted captures | `_INTERNAL/_inbox/` |
| [Your life areas] | [their folders] |

---

## How the System Works

```
CLAUDE.md        — always in context; the map
CONTEXT.md       — per-folder instructions; read when entering a workspace
Skills           — slash-command workflows in .claude/skills/
```

The AI drops into a folder, reads its `CONTEXT.md`, does its work, and exits. It doesn't need to know your whole life — just the area it's working in.

**Capture anything unrouted** to `_INTERNAL/_inbox/`. Triage it later.
