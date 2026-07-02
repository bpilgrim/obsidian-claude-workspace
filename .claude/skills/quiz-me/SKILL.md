---
name: quiz-me
description: Quiz the user on a knowledgebase topic. Use when the user wants to test their understanding or retention of a topic.
argument-hint: [topic] [difficulty: basic|deep|mixed]
allowed-tools: Read
---

Quiz the user on `$0`.

Difficulty: `$1` (default to `mixed` if not provided)

## Steps

1. Read `knowledgebase/topics/$0/manual.md`
2. Read all files in `knowledgebase/topics/$0/notes/`
3. Generate a question bank from this material — do not invent questions about content that isn't in the files

## Question Types by Difficulty

**Basic** — recall and recognition
- "What is [concept]?"
- "What does [term] mean?"
- "Name the steps in [process]"

**Deep** — understanding and application
- "How does [concept A] relate to [concept B]?"
- "Why does [mechanism] work the way it does?"
- "Given [scenario], what would you expect to happen and why?"
- "What's the difference between [X] and [Y]?"

**Mixed** — alternate between basic and deep

## Quiz Format

- Present one question at a time
- Wait for the user's answer before revealing the next
- After each answer:
  - If correct: confirm and add one sentence of reinforcing context from the source material
  - If partially correct: acknowledge what's right, fill in what's missing
  - If incorrect: give the correct answer with a brief explanation grounded in the manual
- Keep a running score: "3 of 5 correct so far"

## After 5 questions

Ask: "Keep going, change difficulty, or focus on a specific section?"

## End of quiz

Summarize:
- Total score
- Which concepts were solid
- Which concepts to review (link to the specific section of `manual.md` or note file)

## Rules

- Only ask about content that exists in the knowledgebase files
- If the manual is too sparse to generate meaningful questions, say so and suggest running `/study-topic $0` first to build the material
- Never repeat a question in the same session
- For metaphysical topics (astrology, astral projection), treat the content as the user's working framework — quiz from their notes, not from general consensus
