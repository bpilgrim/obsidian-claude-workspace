---
name: analyze-job-posting
description: Analyze a job posting against professional experience and resume. Use when a job posting exists in vocation/job-search/opportunities/ and needs an analysis.
argument-hint: [company-role-slug]
allowed-tools: Read, Write
---

Analyze the job posting for opportunity `$0`.

## Steps

1. Read `vocation/job-search/opportunities/$0/posting.md`
2. Read `vocation/professional-experience.md`
3. Read `vocation/resume/master.md`
4. Read `vocation/job-search/_templates/analysis.md` for output format

## Output

Create `vocation/job-search/opportunities/$0/analysis.md` with:

**Skill Alignment Table**
For every required skill, qualification, or experience mentioned in the posting:
- Find direct evidence in `professional-experience.md`
- Rate each as Strong (direct evidence), Partial (adjacent experience), or Gap (no evidence)

**Gaps Section**
List only Gap-rated items. For each, write a gap strategy — how to address it in the application (reframe existing experience, acknowledge and show learning trajectory, minimize).

**Resume Strategy**
Which experiences to lead with, which to cut or compress, what order to present them in for this specific role. Reference specific items from `professional-experience.md` by name.

**Cover Letter Talking Points**
3 themes that connect the candidate's strongest evidence to what the posting most emphasizes. Not generic — grounded in the actual posting language.

**Networking Prompt**
Note any companies, industries, technologies, or names in the posting that appear in `professional-experience.md`. Flag as potential warm-intro opportunities.

## After completing analysis
Remind the user to run `/research-company $0` if not yet done, and `/tailor-resume $0` when ready to apply.
