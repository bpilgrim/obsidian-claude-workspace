---
name: daily-spark
description: Generate a motivational thought for the day, grounded in what's actually on the user's plate. Use when the user needs a spark, a reframe, or an energizing nudge to start moving.
argument-hint: (none required)
allowed-tools: Read, Write, Glob
---

Generate a motivational thought for today.

## Steps

1. Read `coach/profile.md` — who this person is
2. Read the most recent 1–2 files in `coach/sessions/` if any exist — recent context
3. Read `personal-productivity/3_tasks/` — what's on the plate today (look for `bucket: today`)
4. Read `personal-productivity/2_projects/tracks/` — active work tracks and leading edges

## Output

**The Spark**
One thought — not a list, not a pep talk. A single, well-aimed idea that connects who this person is to what they're facing today. It should feel personal, not generic. It can be a reframe, a provocation, a reminder, a metaphor, or an encouragement — whatever the moment calls for.

Keep it under 100 words. Land it and stop.

**Then ask:** "Want to go deeper on anything, or is that enough to get moving?"

## Rules

- No generic motivational quotes — this must be grounded in their actual situation
- Right-brained delivery: use image, metaphor, or narrative, not bullet points
- Don't manufacture urgency — if today is calm, honor that
- Read the energy of what's on their plate and match the tone accordingly
- If profile.md is sparse, work with what's there and note what would make the spark sharper next time

## After the session

If the conversation goes deeper than a spark, save a session:
`coach/sessions/[YYYY-MM-DD]-daily-spark.md`
