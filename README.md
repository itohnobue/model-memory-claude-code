# Model Memory

Persistent memory for [Claude Code](https://claude.ai/download). Two tiers — **knowledge** (permanent facts) + **session** (current task state) — stored as plain Markdown files.

## Why use it

Claude Code forgets everything between sessions and after context compaction. This gives it a memory that survives.

- **Knowledge** — architecture decisions, gotchas, patterns, configs. Write once, recall forever. No rediscovering the same PostgreSQL connection string or Docker incantation.
- **Session** — task plans, todos, progress, blockers. Survives context compaction. Work resumes where it left off.
- **Isolation** — multiple CLI instances or agents work in parallel without conflicting.

## Quick Start

```bash
git clone https://github.com/itohnobue/model-memory-claude-code
cp -R model-memory-claude-code/.claude /path/to/your/project/
cp model-memory-claude-code/CLAUDE.md /path/to/your/project/
```

If you already have a `CLAUDE.md`, append this one instead of overwriting. This teaches Claude Code how and when to use the memory system.

## Commands

```bash
.claude/tools/memory.sh add gotcha "psycopg2 needs libpq-dev" --tags postgres,ubuntu
.claude/tools/memory.sh search "postgres connection"
.claude/tools/memory.sh session add todo "Implement auth middleware" --status pending
.claude/tools/memory.sh session show
```

18 commands total (6 knowledge, 12 session). See `CLAUDE.md` for full usage.

## License

MIT
