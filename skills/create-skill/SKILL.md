---
name: create-skill
description: Create a new agent skill, optionally with a CLI utility and/or persistence layer. Use when you need to teach the agent a repeatable workflow.
---

# Create a Skill Extension

## Structure

```
my-skill/
├── SKILL.md
├── README.md
├── Dockerfile         # if deployment needed
├── packages/
│   ├── core/          # shared logic used by cli and api
│   ├── my-skill-cli/  # if utility needed
│   └── api/           # if persistence needed
└── package.json       # bun workspaces root
```

## Contents

**SKILL.md** — step-by-step instructions for the agent. If a CLI exists, include brief usage examples.

**README.md** — description, prerequisites, install command, usage examples.

**CLI** (if needed):
- TypeScript + Bun, use `commander` for argument parsing
- Named `<skill-name>-cli`, published to npm, runnable via `npx`/`bunx`
- Must include an `install` subcommand that installs the skill into the user's agent by spawning `npx skills add <org/repo>` with `stdio: 'inherit'`
- Compiled to single binary via `bun build --compile`

**API** (if persistence needed):
- PostgreSQL database
- Run locally via `bun run dev`
- `Dockerfile` in root for deployment
- `.env.example` provided

## Checklist

- [ ] `SKILL.md` has valid frontmatter (`name`, `description`)
- [ ] `README.md` with install command and usage examples
- [ ] Shared logic in `core`, imported by both `cli` and `api`
- [ ] `npx my-skill-cli install` installs the skill by delegating to `npx skills add`
- [ ] CLI publishable to npm, `--help` works at root and per-command