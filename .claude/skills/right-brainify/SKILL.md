---
name: right-brainify
description: Re-present information in a right-brained style — metaphor-driven, holistic, narrative, and image-rich. Use when the user wants to understand or internalize something intuitively rather than analytically.
argument-hint: [topic, note name, or paste content]
allowed-tools: Read, Glob
---

Re-present `$ARGS` to make it easier to understand and internalize.

## What This Means

Right-brained does not mean poetic. It means **intuition before mechanics** — give the learner the *why* and the *feel* of a concept before the *how*. The goal is always faster comprehension, not aesthetic transformation.

- **Intuition first** — explain what problem the concept solves before explaining how it solves it
- **Concrete before abstract** — use a real, grounded scenario that *is* the concept, not one that is merely "like" it
- **Analogy only when it maps directly** — an analogy earns its place only if understanding the analogy directly transfers to understanding the concept; otherwise cut it
- **Whole before parts** — show how the pieces relate before drilling into each one
- **Plain language** — if a simpler word exists, use it

## Steps

1. If `$ARGS` is a knowledgebase topic slug, read:
   - `knowledgebase/topics/$ARGS/manual.md`
   - `knowledgebase/topics/$ARGS/notes/` (all files)
2. If `$ARGS` refers to a specific note (e.g. `ai/mcp-servers`), read that file directly from `knowledgebase/topics/`
3. If `$ARGS` is pasted content or a freeform concept, use it as-is

## Presentation Format

**1. The Big Picture**
2–3 sentences. What is this collection of things trying to do? What is the shared problem they solve? No metaphor required — just orient the learner.

**2. Each Concept**
For each item, in this order:
- **Name** (bold, scannable)
- **The problem it solves** — one sentence: "You have X. You need Y. The naive approach is slow/wrong because Z."
- **The core insight** — one sentence: what does this technique realize that makes the problem tractable?
- **In practice** — one sentence: what does using it actually look like?
- **Analogy** — only include if it directly maps to the mechanism and aids understanding; skip it if it would just be decorative

**3. What They Have in Common**
1–2 sentences on the underlying theme connecting the concepts. This is the insight that makes the group make sense as a group.

## Rules

- **Comprehension is the only metric** — every choice should make the concept easier to understand, not more interesting to read
- **Cut any sentence that adds color without adding clarity**
- **Analogies must earn their place** — if removing the analogy makes the explanation clearer, remove it
- Every concept must be scannable — a reader should be able to find and re-read any single concept in isolation
- After presenting, ask: "Does this land? Want me to go deeper on any part?"
