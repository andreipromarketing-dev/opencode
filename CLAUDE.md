# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a **Claude Code plugin** - a collection of production-ready agents, skills, hooks, commands, rules, and MCP configurations. The project provides battle-tested workflows for software development using Claude Code.

## Running Tests

```bash
# Run all tests
node tests/run-all.js

# Run individual test files
node tests/lib/utils.test.js
node tests/lib/package-manager.test.js
node tests/hooks/hooks.test.js
```

## Architecture

The project is organized into several core components:

- **agents/** - Specialized subagents for delegation (planner, code-reviewer, tdd-guide, etc.)
- **skills/** - Workflow definitions and domain knowledge (coding standards, patterns, testing)
- **commands/** - Slash commands invoked by users (/tdd, /plan, /e2e, etc.)
- **hooks/** - Trigger-based automations (session persistence, pre/post-tool hooks)
- **rules/** - Always-follow guidelines (security, coding style, testing requirements)
- **mcp-configs/** - MCP server configurations for external integrations
- **scripts/** - Cross-platform Node.js utilities for hooks and setup
- **tests/** - Test suite for scripts and utilities

## Key Commands

- `/tdd` - Test-driven development workflow
- `/plan` - Implementation planning
- `/e2e` - Generate and run E2E tests
- `/code-review` - Quality review
- `/build-fix` - Fix build errors
- `/learn` - Extract patterns from sessions
- `/skill-create` - Generate skills from git history

## Development Notes

- Package manager detection: npm, pnpm, yarn, bun (configurable via `CLAUDE_PACKAGE_MANAGER` env var or project config)
- Cross-platform: Windows, macOS, Linux support via Node.js scripts
- Agent format: Markdown with YAML frontmatter (name, description, tools, model)
- Skill format: Markdown with clear sections for when to use, how it works, examples
- Skill placement: Curated in skills/; generated/imported under ~/.claude/skills/. See docs/SKILL-PLACEMENT-POLICY.md
- Hook format: JSON with matcher conditions and command/notification hooks

## Contributing

Follow the formats in CONTRIBUTING.md:
- Agents: Markdown with frontmatter (name, description, tools, model)
- Skills: Clear sections (When to Use, How It Works, Examples)
- Commands: Markdown with description frontmatter
- Hooks: JSON with matcher and hooks array

File naming: lowercase with hyphens (e.g., `python-reviewer.md`, `tdd-workflow.md`)

## Skills

Use the following skills when working on related files:

| File(s) | Skill |
|---------|-------|
| `README.md` | `/readme` |
| `.github/workflows/*.yml` | `/ci-workflow` |

When spawning subagents, always pass conventions from the respective skill into the agent's prompt.

### Proactive Skill Suggestions

When the user describes a task that matches a skill's purpose, proactively suggest using it rather than doing the task directly. Examples:

- User says "давай спланируем" or "нужно спланировать" → предложить использовать **writing-plans** скилл
- User says "нужно отладить баг" → предложить **systematic-debugging**
- User says "напиши тесты" → предложить **test-driven-development** или **tdd** workflow
- User says "проведи код-ревью" → предложить **requesting-code-review**
- User asks to test a web page/flow → предложить **Playwright** скилл
- User wants to create API docs → предложить **api-docs-writer**

Just ask "Использовать [скилл] для этого?" before proceeding. The user can always say "да" or "нет".

### Proactive Tips & Life Hacks

When working on a task, occasionally share useful tips they might not know about:

- **Better tools:** Mention if there's a better tool/library for what they're doing (e.g., "Кстати, для этого есть готовый пакет X, не нужно писать вручную")
- **Shortcuts:** Point out if their approach could be simpler (e.g., "Можно проще — использовать npm create за 30 секунд вместо...")
- **Hidden features:** Note interesting features of tools they're using that they might not know
- **Productivity tips:** Share relevant keyboard shortcuts, config tricks, or workflow improvements

Example trigger phrases:
- "Кстати, для [задача] есть инструмент [название]"
- "Не знал? Можно сделать еще проще..."
- "На будущее — вот полезный трюк: [совет]"

This is optional but adds value — the user might not know what questions ask.
