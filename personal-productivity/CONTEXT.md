# personal-productivity

This workspace answers one question: **what should I be working on, and is it moving?**

It does not hold the work itself. It holds the map to the work — track status, project status, and atomic tasks. Actual artifacts (code, drafts, deliverables) live in their respective workspaces and are linked from here.

---

## What Lives Here

| Folder | Contents |
| ------ | -------- |
| `1_goals/` | Long-horizon goals. What success looks like across life areas. |
| `2_projects/tracks/` | One `.md` file per work track. The weekly focus layer. |
| `2_projects/[slug]/` | Non-software project folders with artifacts. |
| `2_projects/[slug].md` | Software project stubs — status + link to `software-engineering/`. |
| `3_tasks/` | Flat `.md` task files. Self-contained, no artifact home needed. |
| `3_tasks/_archive/` | Completed and dropped tasks. |
| `operations/` | Recurring operational workflows (grocery lists, checklists, etc.). |

---

## Work Tracks

Tracks are the strategic lanes of your life. Each track has a file in `2_projects/tracks/track-[name].md`.

**To define your tracks:** think about the distinct types of work you do and what each one is trying to accomplish. Examples:

| Track file | Strategic purpose |
| ---------- | ----------------- |
| `track-job-search.md` | Finding employment |
| `track-freelance.md` | Client income |
| `track-solopreneur.md` | Building products or services |
| `track-learning.md` | Skill development |
| `track-personal.md` | Personal projects and goals |

Create only the tracks you need. Tracks are not mutually exclusive — the same session can serve multiple tracks. The track assignment captures **strategic intent**, not activity type.

Each track file contains:
- **This week's leading edge** — one thing being pushed forward right now
- **Backlog** — next items in rough priority order
- **Blocked / waiting** — stalled items and why
- **Links** — pointers to relevant project folders or workspace files

---

## Project Types

**Non-software project** → folder in `2_projects/[slug]/`
- Has a `README.md` (status, leading edge, backlog)
- Artifacts (drafts, deliverables, notes) live in subfolders

**Software project** → stub file `2_projects/[slug].md`
- Contains: status, track assignment, leading edge, link to `software-engineering/`
- The actual code and technical docs live in `software-engineering/`

---

## Task Format

Tasks are single `.md` files in `3_tasks/`. Named `[slug]-[8-char-id].md`.

Frontmatter fields:
```yaml
type: task
id: [8-char-id]
status: open | focus | done | dropped
area: [life area]
project: [project slug or blank]
track: [track name or blank]
due: [YYYY-MM-DD or blank]
energy: low | medium | high
context: home | office | phone | errands
bucket: today | this-week | next-week | soonish | later  # when you intend to engage; omit if unassigned
completed: [ISO timestamp]                                # stamped when archived
```

**Temporal buckets** — meaning:
- `today` — pool of tasks to choose from today (not a commitment)
- `this-week` — incorporate into this week's plan
- `next-week` — start thinking about approach and where it fits
- `soonish` — definitely want to do, not a priority yet
- `later` — someday / maybe

## Task Lifecycle

```
open → focus → done → _archive/
     ↑_______↓
              → dropped → _archive/
```

**Why archive instead of delete:** completed tasks are a record of momentum. Use the archive during weekly review to see what actually moved.

---

## Agent Instructions

### "What should I work on right now?"
1. Read `2_projects/tracks/` — all track files
2. Find tracks with an active leading edge
3. Check energy/context if provided
4. Return: track name + leading edge item + first next action

### "Plan my week"
1. Read `1_goals/` for current goal state
2. Read all track files in `2_projects/tracks/`
3. Read any project `README.md` files for active projects
4. Synthesize: one leading edge per track, flag anything blocked, suggest which tracks to prioritize

### "What's the status of [project]?"
1. If non-software: read `2_projects/[slug]/README.md`
2. If software: read `2_projects/[slug].md`, then follow link to `software-engineering/`

### Capture / triage an incoming task
1. Determine if it's a task (self-contained) or a project (has artifact gravity)
2. If task: create file in `3_tasks/`, fill frontmatter, assign track if applicable
3. If project: create folder in `2_projects/[slug]/` with `README.md`
4. If software project: create stub in `2_projects/`, create folder in `software-engineering/`

---

## Inbox Routing

Route to `personal-productivity/3_tasks/` when message contains:
- Task-like verbs with no clear domain: "remind me to", "don't forget", "need to", "schedule"

Route to `personal-productivity/2_projects/tracks/` when message contains:
- "this week I'm focusing on", "leading edge", "track update"

Route to `_INTERNAL/_inbox/` if unclear — do not force a classification.
