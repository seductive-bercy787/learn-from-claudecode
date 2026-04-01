---
name: what-would-cc-do
description: "Analyze code and LLM practices against Claude Code's production-grade engineering patterns. Use when the user asks to 'assess my code against Claude Code', 'how would Claude Code do this', 'what patterns does CC use for X', 'review my LLM approach', or invokes /what-would-cc-do:assess or /what-would-cc-do:claudecodefy."
version: 1.0.0
---

# What Would Claude Code Do?

A practice assessment plugin powered by 27 detailed analyses of Claude Code's production engineering patterns (~1,900 TypeScript files, 512K+ lines).

## Commands

| Command | Description |
|---------|-------------|
| `/what-would-cc-do:assess` | Analyze your codebase/work against Claude Code's documented LLM engineering patterns |
| `/what-would-cc-do:claudecodefy` | Apply Claude Code engineering patterns to your code based on assess results |

## When to Trigger

- User asks to evaluate or assess their code, architecture, or LLM practices
- User asks "how would Claude Code do X" or "what would CC do differently"
- User wants to compare their approach against production-grade patterns
- User explicitly invokes `/what-would-cc-do`

## When NOT to Trigger

- General coding questions unrelated to methodology or practice assessment
- User is asking about Claude Code's features as a tool (not its engineering patterns)
- User explicitly asks for help without assessment framing
