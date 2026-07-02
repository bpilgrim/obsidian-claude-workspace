---
name: update-resume
description: Sync the master resume with professional-experience.md. Use when new experience has been added or when the resume needs a refresh.
allowed-tools: Read, Write
---

Update the master resume to reflect the current state of `professional-experience.md`.

## Steps

1. Read `vocation/professional-experience.md` in full
2. Read `vocation/resume/master.md` in full
3. Identify what is in `professional-experience.md` that is not reflected in `resume/master.md`, and vice versa

## Output

Propose a diff — do not overwrite silently. Present:

**Additions** — experience in `professional-experience.md` not yet in the resume
**Updates** — entries that exist in both but where the resume version is outdated or weaker than the source
**Candidates for removal** — resume entries that are old enough or weak enough to reconsider given current positioning

Ask for confirmation before writing changes to `resume/master.md`.

On confirmation, update `resume/master.md` only — never modify `professional-experience.md`.

## Rules

- `professional-experience.md` is the source of truth — the resume is derived from it, not the other way around
- Do not remove experience without explicit user confirmation
- Preserve the existing format and structure of `resume/master.md`
- After updating, note that any tailored resumes in `resume/tailored/` may need to be regenerated
