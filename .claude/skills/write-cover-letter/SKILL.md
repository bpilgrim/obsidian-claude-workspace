---
name: write-cover-letter
description: Write a tailored cover letter for a specific job opportunity. Use after analyze-job-posting and research-company have been run.
argument-hint: [company-role-slug]
allowed-tools: Read, Write
---

Write a tailored cover letter for opportunity `$0`.

## Steps

1. Read `vocation/writing/voice.md` — primary voice guide
2. Read `vocation/job-search/opportunities/$0/analysis.md` — cover letter talking points and skill alignment
3. Read `vocation/job-search/opportunities/$0/company-research.md` — company context and culture signals
4. Read `vocation/job-search/opportunities/$0/posting.md` — role language and requirements
5. Read `vocation/cover-letters/job-search.md` — any additional job-search-specific guidance
6. Read `vocation/resume/tailored/$0.md` if it exists, otherwise `vocation/resume/master.md`

## Output

Create `vocation/job-search/opportunities/$0/cover-letter.md`:

- Opening: connect to the specific company and role — reference something from `company-research.md` that shows genuine interest
- Body (2-3 paragraphs): build on the 3 talking points from the analysis. Lead with strongest alignment. Acknowledge a gap only if it is prominent in the posting and the gap strategy warrants it.
- Closing: clear call to action

## Rules

- Use `vocation/writing/voice.md` as the primary voice guide — it takes precedence over all other tone references
- Ground every claim in `professional-experience.md` — no fabrication
- Write for the specific reader, not a generic recruiter
- Length: 3-4 paragraphs, under 400 words
