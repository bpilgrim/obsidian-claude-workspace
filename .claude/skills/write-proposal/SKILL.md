---
name: write-proposal
description: Write an Upwork bid proposal for a job posting. Use when a new Upwork job has been identified for bidding.
argument-hint: [job-slug]
allowed-tools: Read, Write
---

Write an Upwork bid proposal for `$0`.

## Steps

1. Read `vocation/writing/voice.md` — primary voice guide
2. Read the job description — if a file exists at `vocation/freelance-work/upwork/proposals/$0-posting.md`, read it; otherwise ask the user to paste the job description
3. Read `vocation/cover-letters/upwork.md` — any additional Upwork-specific guidance
4. Read `vocation/resume/master.md` — experience to draw from
5. Read `vocation/professional-experience.md` — for specific project evidence
6. Read `vocation/freelance-work/upwork/operating-checklist.md` — confirm this passed the 60-second qualifier

## Output

Create `vocation/freelance-work/upwork/proposals/[YYYY-MM-DD]-$0.md`:

**Opening line**
Not "I am writing to apply..." — lead with the most relevant thing about the candidate for this specific job. Reference something specific from the posting in the first sentence.

**Body (2-3 paragraphs)**
- Directly address the core need in the posting
- Provide one specific example from `professional-experience.md` that is most relevant
- Address any technical requirements by name

**Closing**
- Clear next step
- Keep it brief — Upwork proposals are skimmed, not read

## Rules

- Upwork tone is direct and confident — not formal, not sycophantic
- Under 300 words — shorter proposals perform better
- Mirror language from the job posting where accurate
- Ground every claim in real experience — no fabrication
- After writing, add a row to the proposal log in `operating-checklist.md`
