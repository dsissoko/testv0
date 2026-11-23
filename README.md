# v0 — Agent-native project template

A portable, stack-agnostic GitHub template for building and operating software with ChatGPT, Claude, Codex, OpenCode or another capable agent. **No application scaffold, provider credentials, or forced framework.**

## Start here

1. Create a repository from this template (or copy its files).
2. Ask your agent to read [AGENTS.md](AGENTS.md), then complete [docs/vision.md](docs/vision.md), [docs/metier.md](docs/metier.md), [docs/fonctionnel.md](docs/fonctionnel.md), [docs/architecture.md](docs/architecture.md) and [docs/roadmap.md](docs/roadmap.md).
3. Choose a stack and integrations only when justified. See the complete [Vercel + Neon webapp example](examples/webapp-vercel-neon.md).
4. Configure GitHub protections, CI and deployment gates using [the setup checklist](docs/operations/github-setup.md).
5. Work in distinct phases: discuss an issue, scope a PR, implement, approve merge, approve release.

## Skills

Eight self-contained, vendor-neutral entry points under `.agents/skills/`:

| Skill | Purpose |
| --- | --- |
| [github](.agents/skills/github/SKILL.md) | Issues, milestones, PR, CI, releases and delivery orchestration |
| [product](.agents/skills/product/SKILL.md) | Vision, domain, UX, requirements, roadmap |
| [engineering](.agents/skills/engineering/SKILL.md) | Architecture, APIs, tests, security, operations |
| [data-management](.agents/skills/data-management/SKILL.md) | Modelling, migrations, reproducible datasets and imports |
| [neon](.agents/skills/neon/SKILL.md) | Optional Neon infrastructure and database branches |
| [vercel](.agents/skills/vercel/SKILL.md) | Optional Vercel previews, deployments and rollback |
| [automation](.agents/skills/automation/SKILL.md) | Recurring agentic tasks, scheduling, monitoring and reporting |
| [promotion](.agents/skills/promotion/SKILL.md) | Optional launch, campaigns, distribution and analytics |

Each skill has a complete procedure and acceptance checks. Read only those relevant to the task. Existing maintained upstream skills can supplement them; do not assume they are installed.

## Core agreements

- Agent-native capability comes first; skills add repeatable constraints, not unnecessary ceremony.
- A skill is **instructions**, a connector/MCP is **access**, and a workflow is **orchestration**.
- GitHub is the durable coordination record; do not rely on remembered conversation state.
- Human authorization is required for merge, release, destructive data operations and outbound promotion.
- CI green, deployment READY, functional QA, merge and release are **different states**.
- Never claim an external action succeeded without verifying its actual result.

See [contributing](CONTRIBUTING.md), [decision records](docs/adr/README.md) and the [skill test plan](docs/operations/agent-evaluation.md).

## Template boundaries

The repository intentionally ships no `package.json`, SQL schema, sample application, live automation, scheduled workflow, secrets or auto-deploy. Those are created when a real project chooses its stack and operating model.

Licensed under [MIT](LICENSE).
