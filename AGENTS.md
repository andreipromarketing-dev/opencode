# Everything Claude Code (ECC) — Agent Instructions

This is a **production-ready AI coding plugin** providing 47 specialized agents, 181 skills, 82 commands, and automated hook workflows for software development.

**Version:** 1.10.0

## Core Principles

1. **Agent-First** — Delegate to specialized agents for domain tasks
2. **Test-Driven** — Write tests before implementation, 80%+ coverage required
3. **Security-First** — Never compromise on security; validate all inputs
4. **Immutability** — Always create new objects, never mutate existing ones
5. **Plan Before Execute** — Plan complex features before writing code

## Available Agents

| Agent | Purpose | When to Use |
|-------|---------|-------------|
| planner | Implementation planning | Complex features, refactoring |
| architect | System design and scalability | Architectural decisions |
| tdd-guide | Test-driven development | New features, bug fixes |
| code-reviewer | Code quality and maintainability | After writing/modifying code |
| security-reviewer | Vulnerability detection | Before commits, sensitive code |
| build-error-resolver | Fix build/type errors | When build fails |
| e2e-runner | End-to-end Playwright testing | Critical user flows |
| refactor-cleaner | Dead code cleanup | Code maintenance |
| doc-updater | Documentation and codemaps | Updating docs |
| cpp-reviewer | C/C++ code review | C and C++ projects |
| cpp-build-resolver | C/C++ build errors | C and C++ build failures |
| docs-lookup | Documentation lookup via Context7 | API/docs questions |
| go-reviewer | Go code review | Go projects |
| go-build-resolver | Go build errors | Go build failures |
| kotlin-reviewer | Kotlin code review | Kotlin/Android/KMP projects |
| kotlin-build-resolver | Kotlin/Gradle build errors | Kotlin build failures |
| database-reviewer | PostgreSQL/Supabase specialist | Schema design, query optimization |
| python-reviewer | Python code review | Python projects |
| java-reviewer | Java and Spring Boot code review | Java/Spring Boot projects |
| java-build-resolver | Java/Maven/Gradle build errors | Java build failures |
| loop-operator | Autonomous loop execution | Run loops safely, monitor stalls, intervene |
| harness-optimizer | Harness config tuning | Reliability, cost, throughput |
| rust-reviewer | Rust code review | Rust projects |
| rust-build-resolver | Rust build errors | Rust build failures |
| pytorch-build-resolver | PyTorch runtime/CUDA/training errors | PyTorch build/training failures |
| typescript-reviewer | TypeScript/JavaScript code review | TypeScript/JavaScript projects |

## Agent Orchestration

Use agents proactively without user prompt:
- Complex feature requests → **planner**
- Code just written/modified → **code-reviewer**

## Proactive Skill Suggestions

When the user describes a task that matches a skill's purpose, proactively suggest using it rather than doing the task directly. Examples:

- User says "давай спланируем" or "нужно спланировать" → использовать **writing-plans** скилл
- User says "нужно отладить баг" → использовать **systematic-debugging**
- User says "напиши тесты" → использовать **test-driven-development**
- User says "проведи код-ревью" → использовать **requesting-code-review**
- User asks to test a web page/flow → использовать **Playwright** скилл
- User wants to document an API → использовать **api-docs-writer**

Ask "Использовать [скилл] для этого?" before proceeding. The user can always say "да" or proceed without it.

## Proactive Tips & Life Hacks

When working on a task, occasionally share useful tips the user might not know about:

- **Better tools:** "Кстати, для этого есть готовый пакет X"
- **Shortcuts:** "Можно проще — использовать npm create за 30 секунд"
- **Hidden features:** Note features of tools they're using they might not know
- **Productivity tips:** Keyboard shortcuts, config tricks, workflow improvements

Example: "Кстати, для [задача] есть инструмент [название]" or "Не знал? Можно сделать еще проще..."

This is optional but adds value — the user might not know what to ask.

## Architecture Patterns

**API response format:** Consistent envelope with success indicator, data payload, error message, and pagination metadata.

**Repository pattern:** Encapsulate data access behind standard interface (findAll, findById, create, update, delete). Business logic depends on abstract interface, not storage mechanism.

**Skeleton projects:** Search for battle-tested templates, evaluate with parallel agents (security, extensibility, relevance), clone best match, iterate within proven structure.

## Performance

**Context management:** Avoid last 20% of context window for large refactoring and multi-file features. Lower-sensitivity tasks (single edits, docs, simple fixes) tolerate higher utilization.

**Build troubleshooting:** Use build-error-resolver agent → analyze errors → fix incrementally → verify after each fix.

## Project Structure

```
agents/          — 47 specialized subagents
skills/          — 181 workflow skills and domain knowledge
commands/        — 82 slash commands
hooks/           — Trigger-based automations
rules/           — Always-follow guidelines (common + per-language)
scripts/         — Cross-platform Node.js utilities
mcp-configs/     — 14 MCP server configurations
tests/           — Test suite
```

`commands/` remains in the repo for compatibility, but the long-term direction is skills-first.

## Success Metrics

- All tests pass with 80%+ coverage
- No security vulnerabilities
- Code is readable and maintainable
- Performance is acceptable
- User requirements are met
