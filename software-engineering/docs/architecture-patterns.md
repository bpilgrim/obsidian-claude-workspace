---
type: reference
updated:
---

# Architecture Patterns

> Patterns and approaches used repeatedly. Read before designing a new system.

---

## Workspace-as-App Pattern

Folder structure + CONTEXT.md files route AI agents without Python pipelines.
- Layer 1: CLAUDE.md (map)
- Layer 2: workspace CONTEXT.md (routing)
- Layer 3: content files (work)

**When to use:** Any AI-assisted workspace or personal tooling.

---

## Thin Transport Layer

Keep capture/delivery mechanisms (bots, APIs) dumb. Intelligence lives in the workspace routing files, not in the transport code. Routing rules evolve by editing markdown — no code changes needed.

**When to use:** Telegram bot, any ingestion pipeline.

---

## (Add patterns as they emerge)
