---
name: distill-source
description: Distill a source (article, video, website, book) into the knowledgebase. Use when the user shares a URL, pastes content, or wants to capture something they've read or watched.
argument-hint: [topic] [url-or-paste]
allowed-tools: Read, Write, WebFetch, WebSearch
---

Distill a source into the knowledgebase for topic `$0`.

## Steps

1. If a URL is provided in `$1`, fetch it with WebFetch and extract the content
2. If content is pasted directly, use that as the source material
3. Read `knowledgebase/_templates/source.md` for output format
4. Read `knowledgebase/topics/$0/manual.md` to understand what's already known — this informs what's new or additive

## Output

Create `knowledgebase/topics/$0/sources/[YYYY-MM-DD]-[source-slug].md`:

**Key Points**
Extract 3–7 of the most important, durable ideas from the source. Write them in your own words — not copy/paste of the original. Each point should be a complete thought.

**Excerpts / Quotes**
Pull 1–3 direct quotes or excerpts that are particularly precise, memorable, or worth preserving verbatim.

**My Take**
Leave this section blank with a prompt — the user fills this in. It's their reaction, not yours.

**Feed Into Manual?**
Assess: does this source contain concepts, explanations, or frameworks that would strengthen `manual.md`? If yes, note which section it would feed into.

## After creating the source file

Ask the user:
1. "Does this look right? Anything to add or correct?"
2. "Should I update the manual with anything from this source?"

If they say yes to the manual update → read the relevant section of `manual.md` and propose an addition without overwriting existing content.

## Rules

- Key points must be in your own words — distillation, not transcription
- Do not fabricate content that isn't in the source
- If the source is a video and only a URL is provided with no transcript available, note what could be extracted from title/description and ask the user to paste key content
- If topic `$0` doesn't exist yet, create the folder structure: `topics/$0/notes/`, `topics/$0/sources/`, `topics/$0/README.md`, `topics/$0/manual.md`
