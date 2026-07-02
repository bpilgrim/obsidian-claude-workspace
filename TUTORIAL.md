# How This Workspace System Works — A Tutorial

> **Optional reading.** If you just want to get started, follow `SETUP.md` and let the AI guide you. Come back here when you want to understand *why* things are structured the way they are.

---

## The Problem This Solves

Most people use AI by opening a chat window, typing a question, getting an answer, and starting over. Each conversation starts from scratch. Context that took ten minutes to explain yesterday has to be explained again today. You paste in the same documents repeatedly. Eventually the conversation gets too long and the AI starts losing track of what was said earlier.

This happens because AI has a **context window** — a limit on how much it can hold in mind at once. Every word you type, every file you paste, every instruction you give costs space in that window. If you dump everything into one conversation, the AI is reading your grocery list while trying to help you write code. You're burning its attention on things that don't matter right now.

The solution isn't a bigger context window. It's **routing** — only giving the AI what it needs for the current task.

---

## The Three-Layer Architecture

This workspace uses three layers, each with a specific job:

```
Layer 1 — CLAUDE.md         Always loaded. The map.
Layer 2 — CONTEXT.md        Loaded per workspace. The room.
Layer 3 — Content files     Loaded as needed. The work.
```

### Layer 1 — The Map (CLAUDE.md)

`CLAUDE.md` is automatically loaded into every conversation. It's always in context, so it should be short and structural — just enough to orient the AI without wasting tokens.

It contains:
- The folder structure (where things live)
- Naming conventions (how files are named)
- The quick navigation table (what task → which folder)

Think of it as the floor plan posted on the wall. The AI walks in, reads it, and immediately knows: *tasks go in `personal-productivity/3_tasks/`, code projects go in `software-engineering/`, unrouted captures go in `_INTERNAL/_inbox/`.*

**Rule:** Don't put detailed instructions in `CLAUDE.md`. Every line costs tokens in every conversation. Keep it as a structural map, nothing more.

### Layer 2 — The Rooms (CONTEXT.md)

Each workspace folder has its own `CONTEXT.md`. This file is only read when the AI is working in that area — so it can be detailed without wasting tokens on other tasks.

A good `CONTEXT.md` tells the AI:
- What lives in this folder
- How the work is organized (stages, file naming, subfolders)
- What to do when given common requests ("when I say 'plan my week', do X")
- What files or skills to use at each stage

When you say *"help me plan my week,"* the AI reads `CLAUDE.md` (layer 1), sees that planning lives in `personal-productivity/`, navigates there, reads that folder's `CONTEXT.md` (layer 2), and then knows exactly what to load and what to do — without you having to explain the system every time.

### Layer 3 — The Work (Content files)

This is everything else: your actual task files, project notes, briefs, specs, journal entries, source notes. The AI reads these only when they're relevant to the current task. A conversation about a software project doesn't load your journal. A conversation about your finances doesn't load your code specs.

**The key insight:** you're not building a system for the AI to read everything. You're building a system that routes the AI to exactly the right thing, every time.

---

## Obsidian: Your Workspace Viewer

This system uses plain folders and markdown files — which means it works with any text editor. But **Obsidian** is the recommended way to open and navigate the vault, for a few reasons:

- It renders markdown beautifully (headers, checkboxes, tables, links all display properly)
- It has a graph view that shows connections between notes
- The **Dataview plugin** can query your files like a database — the task dashboard (`personal-productivity/dashboard.md`) uses this to show your tasks organized by bucket
- It handles internal links (`[[file-name]]`) natively, so you can link between notes without worrying about file paths

**Obsidian is optional.** The AI reads raw markdown files. Every file in this workspace is readable in Notepad, VS Code, or any text editor. You don't need Obsidian to use the system — it just makes the human side of navigating the vault nicer.

To open the workspace in Obsidian: **Open folder as vault** → select the root folder of this repo.

---

## Frontmatter: Structured Metadata in Plain Text

Many files in this system — especially task files — begin with a **frontmatter block**: a section of structured data between `---` delimiters at the very top of the file.

```markdown
---
type: task
id: cf822801
status: open
bucket: this-week
energy: medium
---

# Fix the login bug

- [ ] Reproduce the issue
- [ ] Identify root cause
- [ ] Write the fix
```

The frontmatter block is written in **YAML** — a simple key: value format. Everything between the two `---` lines is metadata. Everything after the second `---` is the normal content of the file.

### Why frontmatter matters

Frontmatter turns a plain text file into a structured record. It gives the AI (and Obsidian's Dataview plugin) a way to:

- **Filter files** — "show me all tasks where `bucket: today`"
- **Sort files** — "show me tasks ordered by `due` date"
- **Update state** — the AI changes `status: open` to `status: done` by editing this block
- **Understand relationships** — a task with `project: my-app` is linked to that project without needing a database

### How the AI uses frontmatter

When the AI creates or modifies a file, it reads and writes the frontmatter directly. For example:

- Capturing a task → creates the file with frontmatter pre-filled from what you told it
- Moving a task to a different bucket → edits `bucket: this-week` to `bucket: today`
- Completing a task → sets `status: done` and adds a `completed` timestamp

The AI never needs to guess where to find this information — it's always at the top of the file in a consistent format.

### How Obsidian uses frontmatter

Install the **Dataview plugin** in Obsidian and you can write queries against frontmatter like this:

```dataview
TABLE status, due
FROM "personal-productivity/3_tasks"
WHERE bucket = "today"
SORT due ASC
```

This renders as a live table of your today tasks inside any Obsidian note — which is exactly how `personal-productivity/dashboard.md` works. The dashboard is just a markdown file full of Dataview queries. Obsidian renders them as live views. The AI updates the underlying files. The dashboard reflects the current state automatically.

### Frontmatter rules

- It must be at the very top of the file — no blank lines before the first `---`
- Keys are lowercase with hyphens, not spaces: `due-date` not `Due Date`
- Values are plain text, numbers, or booleans (`true`/`false`)
- The AI will only modify frontmatter fields it owns — it will not touch fields it doesn't recognize

---

## Naming Conventions as a Lightweight Database

One of the most underrated features of this system is that **the AI can find files by name** — no database, no search index, no custom integration required.

When you ask *"pull up the spec for my auth feature,"* the AI doesn't need to scan every file. It knows from the naming convention that a spec lives at `software-engineering/workflows/02-specs/[project]-auth-spec.md`. It navigates there directly.

This only works if names are consistent. That's why `CLAUDE.md` includes naming conventions. A file named `auth spec final v3 REVISED.docx` is invisible to this system. A file named `my-app-auth-spec.md` in the right folder is always findable.

**Practical rule:** when you create a file, ask yourself — could the AI find this from its name and location alone, without searching?

---

## Skills: Reusable Workflows

Skills (in `.claude/skills/`) are slash commands that run a predefined workflow. Instead of explaining a multi-step process every time, you capture it once as a skill and invoke it with a short command.

Examples:
- `/write-brief my-project` — kicks off the project planning pipeline
- `/distill-source` — extracts key ideas from an article you paste in
- `/code-review my-project` — reviews code against the spec

Skills work best when wired into a workspace. A skill that runs in isolation is just a reusable prompt. A skill invoked from within a workspace — where the AI already has context from the `CONTEXT.md` — is a step in a pipeline.

The `software-engineering/` workspace is the clearest example: the skills (`/write-brief`, `/develop-requirements`, `/plan-architecture`, etc.) map to the stages of the pipeline defined in `software-engineering/CONTEXT.md`. Each skill knows what to read, what to produce, and where to put it.

---

## The Workspace as Your App

Here's the reframe that makes this click: **the folder is your app. The files are your UI.**

You don't need a web dashboard, a database, a Python backend, or a custom agent framework. You need:
- A folder structure that mirrors how you think about your work
- `CONTEXT.md` files that tell the AI how each area works
- Naming conventions so files can be found without searching
- Skills for the parts of your workflow that repeat

The AI becomes whatever kind of assistant you need, depending on which workspace you're in. In `software-engineering/` it's a technical co-builder. In `personal-productivity/` it's a planning partner. In `journal/` it's a reflective listener. Same AI, different room, different role — because each room has different instructions.

---

## How to Make This Yours

The workspaces and workflows included in this repo are starting points, not prescriptions. The structure that works for a software developer won't look the same as the structure for a freelance designer, a student, or someone managing a household.

**The questions to ask:**

1. **What are the distinct areas of my life that generate work or notes?**
   These become your top-level folders: `vocation/`, `health/`, `creative-work/`, `clients/`, etc.

2. **What do I do repeatedly that has multiple steps?**
   These become systematized workflows with staged folders and `CONTEXT.md` pipeline instructions.

3. **What do I ask the AI to do more than twice?**
   These become skills — slash commands that encode the process once so you never explain it again.

4. **What information does the AI always need vs. only sometimes?**
   Always → goes in `CLAUDE.md`. Sometimes → goes in a workspace `CONTEXT.md`. Rarely → lives in content files, loaded on demand.

Start with two or three workspaces. Get a feel for how the routing works. Then expand. The system grows with you — adding a workspace is just creating a folder with a `CONTEXT.md`.

---

## A Day in the Life

To make this concrete, here's what a typical interaction looks like once the system is set up:

**Morning planning:**
> *"What should I work on today?"*

The AI reads `CLAUDE.md`, routes to `personal-productivity/`, reads its `CONTEXT.md`, reads the track files, and returns a prioritized plan. You didn't explain anything. You didn't paste any context. It just worked.

**Starting a project:**
> *"/write-brief my-new-app"*

The AI invokes the `write-brief` skill, reads `software-engineering/CONTEXT.md` for pipeline conventions, interviews you, and creates `software-engineering/workflows/01-briefs/my-new-app-brief.md`. The file lands in the right place with the right name.

**Capturing something unrouted:**
> *"Remember to call the electrician Tuesday"*

If you have a bot or quick-capture setup, it routes to `_INTERNAL/_inbox/`. If not, the AI creates a task file in `personal-productivity/3_tasks/`. Either way, it doesn't ask you where to put it.

**Picking up where you left off:**
> *"Where were we on the auth feature?"*

The AI reads `software-engineering/PROJECTS.md`, finds the project, reads the build notes, and tells you exactly what was in progress and what the next step was.

---

## Further Reading

The core ideas here are not new. They come from decades of software engineering thinking about separation of concerns, modular design, and routing — applied to the problem of working with AI.

The workspace concept was inspired by the video *"Stop Building AI Agents. Use This Folder System Instead."* ([YouTube](https://www.youtube.com/watch?v=MkN-ss2Nl10)), which walks through the three-layer architecture and the reasoning behind it.

The short version: folders and markdown files, written in plain English, are more durable and more flexible than most AI frameworks being built today. The folder is your app. The work is the point.
