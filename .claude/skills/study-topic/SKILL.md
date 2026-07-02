---
name: study-topic
description: Study a knowledgebase topic in a structured, digestible session. Use when the user wants to learn, review, or go deeper on a topic.
argument-hint: [topic]
allowed-tools: Read
---

Run a study session on `$0`.

## Steps

1. Read `knowledgebase/topics/$0/README.md` — understand scope and subtopics
2. Read `knowledgebase/topics/$0/manual.md` — primary study material
3. Read all files in `knowledgebase/topics/$0/notes/` — supporting reference
4. Read the 3 most recent files in `knowledgebase/topics/$0/sources/` — recent captures for context

## Presentation Format

Structure the session in layers — never dump everything at once:

**Layer 1 — Orientation (always start here)**
- What is this topic?
- Why does it matter?
- How does it connect to what the user already knows? (Check if related topics exist in `knowledgebase/topics/` and draw analogies)

**Layer 2 — Core Concepts**
- Present the 3–5 most fundamental ideas from the manual
- Use plain language first, then precise language
- One concept at a time — pause and ask "ready to continue?" after each if the topic is complex

**Layer 3 — How It Works**
- Mechanisms, processes, relationships between concepts
- Use examples grounded in the source material

**Layer 4 — Depth and Nuance**
- Edge cases, common misconceptions, open questions
- What the manual says vs. what remains uncertain

## After presenting

Say: "That's the core of what you have on [topic]. Want me to quiz you, go deeper on any section, or connect this to another topic?"

## Rules

- Teach from what's in the knowledgebase — don't supplement heavily from general knowledge
- If the manual is sparse, say so: "Your manual on this is still early — here's what you have so far. Want to build it out?"
- Match depth to what's actually in the files — don't fake completeness
- If the user already knows parts of the topic, skip those layers when they say so
