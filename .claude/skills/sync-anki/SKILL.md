---
name: sync-anki
description: Sync knowledgebase content to Anki flashcards via the ai-assistant-v2 MCP tool.
argument-hint: [topic-slug | blank for all]
allowed-tools: mcp__ai-assistant-v2__sync_anki
---

Sync knowledgebase content to Anki.

## Pre-flight

Before calling the tool, confirm:
1. Anki is currently running on this machine
2. The AnkiConnect add-on is installed (https://ankiweb.net/shared/info/2055492159)

If the user hasn't confirmed these, ask before proceeding.

## Steps

If `$ARGS` is a topic slug (e.g. `ai`, `astrology`, `python`):
- Call `sync_anki` with `topic: "$ARGS"`

If `$ARGS` is blank:
- Call `sync_anki` with no arguments (syncs all topics)

## After syncing

Report the result summary from the tool. If errors occurred, note that Anki may not have
been running or AnkiConnect may not be installed.

Say: "Sync complete. Open Anki and browse the `Knowledgebase` deck to review new cards."
