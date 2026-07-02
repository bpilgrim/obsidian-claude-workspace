---
name: design-agent
description: Design an AI agent system — tools, memory, context flow, and orchestration. Use when a project involves an LLM making decisions across multiple steps or managing state.
argument-hint: [project-slug] [agent-name]
allowed-tools: Read, Write, Glob
---

Design the agent architecture for `$0` — agent: `$1`.

## Steps

1. Read `software-engineering/workflows/02-specs/$0-spec.md`
2. Read `software-engineering/docs/tech-standards.md` — note default model (claude-sonnet-4-6) and stack
3. Read `software-engineering/workflows/03-builds/$0/architecture.md` if it exists
4. Read any existing prompt design files at `software-engineering/workflows/03-builds/$0/prompt-design-*.md`
5. Understand: what is the agent's job? What does it decide? What can it act on?

## Output

Create `software-engineering/workflows/03-builds/$0/agent-design-$1.md`:

```markdown
# [Project Name] — Agent Design: $1

**Slug:** $0
**Agent:** $1
**Model:** claude-sonnet-4-6
**Date:** [YYYY-MM-DD]

---

## Agent Purpose

[One paragraph: what this agent does, what decisions it makes, and what outcomes it produces]

## Agent Type

- [ ] Single-turn (one prompt → one response, no state)
- [ ] Multi-turn conversational (maintains dialogue state)
- [ ] Agentic loop (LLM calls tools, evaluates results, continues until done)
- [ ] Orchestrator (routes work to sub-agents)
- [ ] Sub-agent (receives tasks from an orchestrator)

## Inputs

| Input | Source | Description |
| ----- | ------ | ----------- |
| [name] | [user / file / DB / webhook / prior agent] | [what it contains] |

## Tools / Capabilities

| Tool | When the agent uses it | What it returns |
| ---- | ---------------------- | --------------- |
| [tool_name] | [condition] | [output type] |

## Memory and Context

| What | Where it lives | How long |
| ---- | -------------- | -------- |
| [Conversation history] | [in-context / external store] | [per-session / persistent] |
| [User preferences] | [file / DB] | [persistent] |
| [Task state] | [_state.json / DB] | [per-task] |

## Decision Flow

```
[Input received]
  ↓
[Agent evaluates: condition]
  ├── [Branch A] → [action/tool]
  └── [Branch B] → [action/tool]
       ↓
[Agent synthesizes result]
  ↓
[Output to: user / file / next agent]
```

## System Prompt Design

**Persona / role:** [how the agent should present itself]
**Constraints:** [what it must never do]
**Output format:** [what it must always produce]

See `prompt-design-$1.md` for full prompt text (create with `/design-prompt $0 $1`).

## Failure Modes and Guards

| Failure | Detection | Recovery |
| ------- | --------- | -------- |
| [Hallucination] | [output validation] | [retry / fallback / human escalation] |
| [Tool failure] | [exception / timeout] | [retry / skip / error message] |
| [Infinite loop] | [step counter] | [force-exit after N steps] |
| [Off-task behavior] | [output classifier] | [re-anchor with system prompt] |

## Human-in-the-Loop Points

[Where does the agent pause and wait for human input or approval before continuing?]

- [ ] [Decision point 1 — why human judgment is needed here]
- [ ] [Decision point 2]

## Integration Points

| System | How the agent connects | Direction |
| ------ | ---------------------- | --------- |
| [Telegram / API / file system] | [webhook / polling / direct call] | [input / output / both] |

## Evaluation

How do you know the agent is doing its job?

| Metric | How to measure | Target |
| ------ | -------------- | ------ |
| [Task completion rate] | [% of tasks completed without human correction] | [>90%] |
| [Latency] | [time from input to output] | [<N seconds] |

## Open Questions

- [ ] [Design decision not yet made]
```

## After writing

Say: "Agent design documented. Next: `/design-prompt $0 $1` to write the full system prompt, or `/write-tests $0` to spec evaluation test cases."

## Rules

- Be explicit about human-in-the-loop points — autonomous agents should have clear escalation paths
- Document failure modes before they happen, not after
- If this agent is part of a multi-agent system, map how it connects to the orchestrator and other sub-agents
- Ground tool choices in what actually exists or can be built — don't design tools that are aspirational
