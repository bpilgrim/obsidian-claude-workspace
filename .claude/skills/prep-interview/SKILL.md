---
name: prep-interview
description: Generate interview prep for a job opportunity. Use when an opportunity has advanced to phone screen or interview stage.
argument-hint: [company-role-slug]
allowed-tools: Read, Write
---

Generate interview prep for opportunity `$0`.

## Steps

1. Read `vocation/job-search/opportunities/$0/analysis.md`
2. Read `vocation/job-search/opportunities/$0/company-research.md`
3. Read `vocation/job-search/opportunities/$0/posting.md`
4. Read `vocation/professional-experience.md` for specific story material
5. Read `vocation/job-search/_templates/interview-prep.md` for output format

## Output

Create or populate `vocation/job-search/opportunities/$0/interview-prep.md`:

**Role-Specific Talking Points**
3 themes drawn from the cover letter talking points in the analysis. These are the narrative threads to weave throughout the interview.

**Likely Questions**
Generate 8-12 questions likely to be asked, based on:
- The role requirements in the posting
- Common questions for this role type
- Any gaps identified in the analysis (they will probe these)

For each question, draft a concise answer grounded in `professional-experience.md`. Use the STAR format (Situation, Task, Action, Result) for behavioral questions.

**Questions to Ask Them**
5 thoughtful questions that show genuine interest. Draw from `company-research.md` — reference something specific, not generic.

**Logistics**
Leave format, interviewer, date/time, and platform blank — to be filled in when the interview is scheduled.

## Rules

- Answers must reference real experience from `professional-experience.md` — no invented stories
- Flag any question that probes a known gap from the analysis so the candidate is prepared
