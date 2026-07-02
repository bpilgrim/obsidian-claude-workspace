---
name: plan-day
description: Daily planning session — decompose today's tasks into steps, then build a committed list from what you can realistically finish. Use at the start of the day or whenever the plan needs reforming.
argument-hint: (none required)
allowed-tools: Read, Write, Glob, Bash
---

Run an interactive daily planning session.

## Steps

1. Read all task files in `personal-productivity/3_tasks/` — collect tasks where `bucket: today`
2. Call `get_calendar_events` with `days: 1` — know what time is actually available today
3. Present the **Opening View** and enter the planning loop

---

## Opening View

Show:

**Today's Pool** — all `bucket: today` tasks, with their current decomposition status:
- *(decomposed)* — already has checklist steps in the body
- *(not decomposed)* — no steps yet

**Calendar** — one-line summary of today's events and approximate blocked time (e.g. "2 events — IEP Meeting 1:45pm, Plan day 9am").

Say: "Let's decompose your tasks first, then figure out what you're committing to. Want to go through them one by one, or jump straight to a specific one?"

---

## Phase 1: Decomposition

For each task (in order, or as the user directs):

1. Show the task title and existing body/steps if any
2. If already decomposed, ask: "These steps exist — want to revise them or keep them?"
3. If not decomposed, ask: "What are the steps for [task]?" — or offer to suggest steps if the task is clear enough to reason about
4. Write steps as a markdown checklist in the task body:
   ```
   - [ ] Step one
   - [ ] Step two
   - [ ] Step three
   ```
5. Confirm: "✓ [N] steps added to [task title]."

After decomposing, immediately ask: **"How many of these steps can you realistically do today — all of them, or just some?"**

- **All** → the whole task is in scope for commitment
- **Some** → ask which ones (by number or description) → note the today-scope

Move to the next task.

When all tasks have been decomposed (or skipped), say: "All decomposed. Ready to build your committed list?"

---

## Phase 2: Building the Committed List

Show a summary table:

| Task | Steps | Today's Scope |
|------|-------|---------------|
| Respond to Emerson Finaid | 2 steps | All |
| Submit job application to Matheny | 4 steps | Steps 1–3 |
| Basement Office Cleanup | 5 steps | Not set |

For any task with no scope set yet, ask: "What's your scope on [task]?"

As scopes are set, the committed list takes shape. The user can say "remove [task]" to pull it out entirely.

**Gut-check** (offer once when list is taking shape):
"Looking at your calendar and these tasks — does this feel like a realistic day, or do you want to trim?"
Don't repeat if they've already responded.

---

## Phase 3: Locking In

When the user says **done**, **good**, **looks good**, or similar:

For each committed task:
1. Set `focus: true` in frontmatter
2. If partial scope, add a `today_scope` field to frontmatter with the scope description (e.g. `today_scope: "steps 1-3"`)

For any previously-committed task removed from today's list:
- Remove `focus: true` and `today_scope` from frontmatter

Show the final committed list:
```
✓ Committed for today:
  • Respond to Emerson Finaid — all 2 steps
  • Submit job application to Matheny — steps 1–3
```

Say: "You're set. Good luck today."

---

## Reforming the List

The user can re-enter planning at any time to adjust. On re-entry:
1. Show current committed list (tasks with `focus: true`)
2. Show remaining pool
3. Ask: "What do you want to change?"

Support: adding tasks, removing tasks, changing step scope on any committed task.

---

## Frontmatter Updates

**Committing a task (full scope):**
```yaml
focus: true
```

**Committing a task (partial scope):**
```yaml
focus: true
today_scope: "steps 1-3"
```

**Uncommitting:**
Remove `focus` and `today_scope` lines entirely.

---

## Rules

- Decompose before committing — don't let the user commit to a whole task without knowing what's in it
- Commitment is at the step level, not just the task level — "I'm doing steps 1–3" is a valid commitment
- Never auto-commit anything — every committed item is an explicit user choice
- If the pool is empty, say so and ask if they want to pull from this-week or unassigned
- If a task the user wants to work on isn't in today's pool, offer to move it to `bucket: today` first
- Keep the display clean after each change
- Match the user's energy — fast or deliberate
