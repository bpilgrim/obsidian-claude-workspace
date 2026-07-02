---
name: tailor-resume
description: Tailor the master resume for a specific job opportunity. Use after analyze-job-posting has been run.
argument-hint: [company-role-slug]
allowed-tools: Read, Write
---

Tailor the master resume for opportunity `$0`.

## Steps

1. Read `vocation/resume/master.md`
2. Read `vocation/job-search/opportunities/$0/analysis.md` — specifically the Resume Strategy section
3. Read `vocation/job-search/opportunities/$0/posting.md` for language and keywords
4. Read `vocation/professional-experience.md` if additional detail is needed

## Output

Create `vocation/resume/tailored/$0.md`:

- Start from the full content of `resume/master.md`
- Apply the resume strategy from the analysis: reorder, emphasize, compress, or cut as recommended
- Mirror language from the job posting where it accurately describes the candidate's experience — do not fabricate
- Do not add experience that does not exist in `professional-experience.md`
- Do not modify `resume/master.md`

## Rules

- The tailored resume must be truthful — only reframe, never invent
- Keep the same format and structure as `resume/master.md`
- Note at the top of the file: `Tailored for: [company] — [role]` and the date
