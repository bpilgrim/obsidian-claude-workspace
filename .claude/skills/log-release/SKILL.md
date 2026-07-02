---
name: log-release
description: Create a release log entry for a software project version. Use when shipping a version — captures what changed, what's known broken, and what's next.
argument-hint: [project-slug] [version]
allowed-tools: Read, Write, Glob, Grep
---

Log release `$1` for `$0`.

## Steps

1. Read `software-engineering/PROJECTS.md` — find the project entry and current version
2. Check for existing releases in `software-engineering/workflows/03-builds/$0/release/` — read the most recent one for context
3. Read recent build notes or spec if available to understand what changed
4. Ask the user: "What changed in this release? What's still broken? What's next?" — or use git log if available

## Output

Create `software-engineering/workflows/03-builds/$0/release/$0-v$1.md`:

```markdown
# [Project Name] v$1 — Release Log

**Date:** [YYYY-MM-DD]
**Status:** [released | pre-release | yanked]
**Slug:** $0

---

## What's in this release

### Added
- [New feature or capability]

### Changed
- [Modification to existing behavior]

### Fixed
- [Bug or issue resolved]

### Removed
- [Feature or capability removed]

## Known issues

- [ ] [Issue description — link to debug-issue or spec if tracked]

## Breaking changes

[Any change that requires the caller or user to change their behavior. "None" if clean upgrade.]

## How to upgrade

[Steps required to go from previous version to this one. "None" if drop-in.]

## What's next

- [ ] [Planned for next release]
- [ ] [Backlog item surfaced during this release]

## Notes

[Anything worth knowing about this release that doesn't fit above — deployment context, dependencies updated, performance observations]
```

## After writing

Update `software-engineering/PROJECTS.md` — change the version number for this project to `$1`.

Say: "Release $1 logged. Consider running `/lessons-learned $0` to capture what you'd do differently."

## Rules

- Use semantic versioning: MAJOR.MINOR.PATCH — MAJOR for breaking changes, MINOR for new features, PATCH for fixes
- Known issues must be honest — don't ship a release log that pretends everything is working
- Keep "What's next" grounded in real plans, not wishlist items
