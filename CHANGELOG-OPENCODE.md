# Changelog - OpenCode Dev Configuration

> Last updated: 2026-04-07
> Backup: `.opencode.backup-v2/`

---

## v2.0.0 (Current) — Enhanced Configuration

### What's Different from Main Repo

| Feature          | Main Repo            | Our Config             |
| ---------------- | -------------------- | ---------------------- |
| **Agents**       | None                 | 24 subagents           |
| **Commands**     | ~6                   | 39 commands            |
| **MCP**          | None (except pencil) | MemPalace integrated   |
| **Instructions** | Minimal              | Full INSTRUCTIONS.md   |
| **Skills**       | 100+ (skills/skills) | 100+ + 8 core from ECC |

---

## Installed Components

### 24 Agents (.opencode/agent/)

- `planner` — Expert planning specialist
- `architect` — Software architecture specialist
- `tdd-guide` — TDD workflow enforcer
- `code-reviewer` — Code quality & security
- `security-reviewer` — Vulnerability detection
- `build-error-resolver` — Build/TypeScript fixes
- `e2e-runner` — Playwright E2E testing
- `doc-updater` — Documentation specialist
- `refactor-cleaner` — Dead code cleanup
- `go-reviewer` / `go-build-resolver` — Go specialists
- `database-reviewer` — PostgreSQL expert
- `cpp-reviewer` / `cpp-build-resolver` — C++ specialists
- `java-reviewer` / `java-build-resolver` — Java specialists
- `kotlin-reviewer` / `kotlin-build-resolver` — Kotlin specialists
- `python-reviewer` — Python specialist
- `rust-reviewer` / `rust-build-resolver` — Rust specialists
- `docs-lookup` — Context7 documentation lookup
- `harness-optimizer` — Agent harness optimization
- `loop-operator` — Autonomous loop operator

### 39 Commands (.opencode/command/)

- `/plan`, `/tdd`, `/code-review`, `/security`, `/build-fix`
- `/e2e`, `/refactor-clean`, `/orchestrate`, `/learn`
- `/checkpoint`, `/verify`, `/eval`, `/update-docs`
- `/update-codemaps`, `/test-coverage`, `/setup-pm`
- `/go-review`, `/go-test`, `/go-build`, `/skill-create`
- `/instinct-status`, `/instinct-import`, `/instinct-export`
- `/evolve`, `/promote`, `/projects`, `/harness-audit`
- `/loop-start`, `/loop-status`, `/quality-gate`, `/model-route`
- - оригинальные: `/ai-deps`, `/commit`, `/issues`, `/rmslop`, `/spellcheck`

### MCP Integration

- **MemPalace** — AI memory system
  - Path: `D:/MY-LIFE-SYSTEM/mempalace-main/mempalace/mcp_server.py`
  - Tools: search, status, add_drawer, diary_write/read

### Instructions (.opencode/instructions/)

- `INSTRUCTIONS.md` — Comprehensive development guidelines
  - Security mandatory checks
  - Code style preferences
  - MemPalace workflow integration

### Skills (skills/skills/)

- 8 core from ECC:
  - `tdd-workflow/`
  - `security-review/`
  - `coding-standards/`
  - `frontend-patterns/`
  - `backend-patterns/`
  - `e2e-testing/`
  - `api-design/`
- 100+ original in `skills/skills/`

---

## Memory (MemPalace)

### Structure

- **Wing:** `moi_proekty` — все проекты пользователя
- **Rooms:** general, opencode-dev, ecc-integration, mempalace-setup

### Usage

1. **Before session:** Check status, search relevant memories
2. **During session:** Save key decisions via `mempalace_add_drawer`
3. **After session:** Save summary via `mempalace_diary_write`

### Available Tools

- `mempalace_search` — Semantic search
- `mempalace_status` — Palace stats
- `mempalace_list_wings` — All wings
- `mempalace_list_rooms` — Rooms in wing
- `mempalace_add_drawer` — Add content
- `mempalace_diary_write/read` — Agent diary (AAAK format)

---

## Cleanup Performed

Removed duplicate directories:

- `D:\everything-claude-code\` (cloned repo)
- `D:\GITINSTALL\opencode-dev\everything-claude-code\` (duplicate)

---

## Files

```
D:\GITINSTALL\opencode-dev\
├── .opencode/
│   ├── opencode.jsonc      # Main config (448 lines)
│   ├── agent/              # 24 agent prompts
│   ├── command/            # 39 command templates
│   ├── instructions/       # INSTRUCTIONS.md
│   └── tool/               # github-triage.ts, github-pr-search.ts
├── skills/
│   └── skills/             # 100+ skills
├── CHANGELOG-OPENCODE.md   # This file
└── .opencode.backup-v2/    # Backup
```

---

## Original State (v1.0.0)

See git history for original config before enhancements.
