# what-would-cc-do — Plugin Documentation

## Overview

**what-would-cc-do** analyzes your codebase and LLM practices against production-grade engineering patterns extracted from Claude Code's source code (~1,900 TypeScript files, 512K+ lines). It identifies gaps, presents trade-offs, and optionally applies improvements.

## Commands

| Command | Description |
|---------|-------------|
| `/what-would-cc-do:assess` | Analyze your code against Claude Code's patterns. Outputs gaps with pros/cons. |
| `/what-would-cc-do:claudecodefy` | Apply selected improvements from a prior `:assess` session. |

## Workflow

```
:assess → [gap analysis with pros/cons] → [user selects gaps] → :claudecodefy → [apply changes]
```

1. Run `:assess` with a description of what you're working on (or let it ask)
2. Review the gap analysis — each gap shows CC's approach, your approach, and trade-offs
3. Select which gaps to pursue (all, high-impact only, specific ones, or none)
4. Run `:claudecodefy` to apply the selected improvements
5. Review the changes and verification results

## Knowledge Base

The KB is the 27 `claude_code_*.md` files in this repository, covering:

| Category | Files |
|----------|-------|
| Core Architecture | 01 (overview), 02 (query engine), 16 (performance) |
| Prompt Engineering | 03 (prompts), 20 (extended thinking), 23 (caching) |
| Tool & Agent Design | 04 (tools), 10 (multi-agent), 11 (MCP) |
| Reliability | 07 (retry), 08 (streaming), 09 (security) |
| System Design | 12 (commands), 14 (state), 15 (config), 19 (hooks) |
| Integration | 13 (terminal UI), 17 (IDE bridge), 21 (plugins) |
| Best Practices | 18 (patterns & lessons), 22 (CLAUDE.md), 24 (testing), 25 (supplementary) |

The **kb-reader** agent reads only the 2-4 files relevant to each assessment, keeping context usage efficient.

## Assessment Categories

- Architecture / Modularity
- Prompt Engineering
- Tool / API Design
- Error Handling / Resilience
- Context Management
- Security
- Multi-Agent / Orchestration
- Testing / Evaluation
- State / Configuration
- UI / UX
- Hooks / Plugins / Extensibility
- Performance

## Design Principles

1. **CC patterns are reference, not gospel.** Your approach may be better for your context.
2. **Trade-offs are always presented.** Every recommendation includes pros AND cons.
3. **Zero gaps is a valid result.** If your approach already aligns, the plugin says so.
4. **Option-based interaction.** You always have choices — nothing is forced.
5. **Self-contained.** No external databases, API keys, or dependencies required.

## Installation

```
/plugin marketplace add nathanyjleeprojects/learn-from-claudecode
/plugin install what-would-cc-do@learn-from-claudecode
```

## Architecture

```
.claude-plugin/
├── plugin.json              # Plugin manifest
└── marketplace.json         # Marketplace registry
skills/what-would-cc-do/
└── SKILL.md                 # Trigger definitions
commands/
├── assess.md                # :assess command
└── claudecodefy.md          # :claudecodefy command
agents/
└── kb-reader.md             # KB retrieval subagent
claude_code_*.md             # Knowledge base (27 files)
```

The kb-reader agent discovers `claude_code_*.md` files via glob pattern, works regardless of install location (local dev or marketplace cache).
