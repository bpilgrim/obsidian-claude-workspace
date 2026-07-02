---
name: research-company
description: Research a company and populate the company-research file for a job opportunity. Use when a new opportunity has been qualified.
argument-hint: [company-role-slug]
allowed-tools: Read, Write, WebSearch, WebFetch
---

Research the company for opportunity `$0`.

## Steps

1. Read `vocation/job-search/opportunities/$0/posting.md` — extract company name, any signals about size, stage, tech stack, mission
2. Search the web for: company name + "about", recent news, engineering blog if relevant, Glassdoor culture signals, LinkedIn company page
3. Read `vocation/job-search/_templates/company-research.md` for output format

## Output

Create or populate `vocation/job-search/opportunities/$0/company-research.md`:

- **What They Do** — one clear sentence. What product or service, for whom.
- **Who They Serve** — customer type (enterprise, SMB, consumer, developer, etc.)
- **Size / Stage** — headcount range, funding stage or public status if known
- **Tech Stack** — languages, frameworks, platforms mentioned in posting or engineering blog
- **Recent News** — anything in the last 6 months worth knowing (funding, product launches, layoffs, leadership changes)
- **Culture Signals** — Glassdoor themes, how they describe themselves in the posting, what they emphasize in values
- **Why This Role Exists** — infer from posting: backfill, growth, new initiative?

## Rules

- Note source and date for any factual claim
- If information is not findable, say so — do not guess
- Keep each section brief — this is reference material, not a report
