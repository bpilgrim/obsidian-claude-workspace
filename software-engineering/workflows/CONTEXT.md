# workflows

The active pipeline for software projects. These folders only hold in-progress work.

| Stage | Folder | File pattern | Purpose |
| ----- | ------ | ------------ | ------- |
| 1 | `01-briefs/` | `[slug]-brief.md` | What to build, why, success criteria |
| 2 | `02-specs/` | `[slug]-spec.md` | Requirements spec |
| 2 | `02-specs/` | `[slug]-architecture.md` | System architecture (components, data flow, decisions) |
| 2 | `02-specs/` | `[slug]-frontend-design.md` | Screens, flows, components — run when brief has UI |
| 2 | `02-specs/` | `[slug]-api-design.md` | API contract — run when brief has an API boundary |
| 3 | `03-builds/` | `[slug]-notes.md` | Dev journal, decisions, blockers |

**Feature work** on an existing project uses a compound slug: `[project]-[feature]-brief.md`, etc.

**On release**, all three artifacts move to `../release/[project]/v[version]/` — the workflow folders stay clean. Current stage is always tracked in `../PROJECTS.md`.
