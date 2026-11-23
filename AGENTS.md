# AGENTS.md — Portable agent working agreement

This file applies to all AI agents and human contributors. Read the active project docs before making decisions. Skills are under `.agents/skills/<name>/SKILL.md`; discover and load **only relevant** skills. Their procedures complement native agent reasoning, never replace it. Prefer the simplest effective method satisfying the same invariants. Do not assume a particular model, CLI, MCP or connector exists; check availability and permissions.

## Authority and continuity

GitHub code, issues, PRs, checks and current project docs are the durable source of truth, not conversation memory. Inspect the actual state before claiming progress. The active docs index is `docs/README.md`. Keep code, data model, APIs, tests, docs and operations consistent in the same PR. Record consequential decisions in `docs/adr/`.

## Four authorization boundaries

1. **Discuss / issue**: clarify need, search for duplicates, propose acceptance criteria. Create/update an issue only with approval; no code or PR implied.
2. **Scope PR**: select coherent issues, dependencies, acceptance criteria, risks, test and rollout plan. No implementation implied.
3. **Implement PR**: only when authorized; branch from current main, make changes, test, document, open PR, inspect CI and previews. **Never push directly to main.** Merge requires explicit approval.
4. **Release**: a distinct explicit approval. Check deployed environment, migrations, data safety, smoke tests, rollback and version. A merge is not itself permission to publish.

For partial work use `Refs #N`; use `Closes #N` only when the issue is fully resolved. A PR may cover several issues; an issue may span several PRs. Milestones represent product deliverables and are not automatically semantic versions.

## Safety and quality

Never fabricate tests, checks, external actions, provenance or URLs. Treat secrets, user data, destructive SQL, costs, public posts and third-party messages as sensitive. Prefer least privilege, dry-run, idempotency and reversible changes. Explicitly verify target environment before write. CI green ≠ preview tested ≠ production deployed. Verify actual GitHub/Vercel triggers; instructions alone cannot prevent automatic deployments.

## Skills routing

- Product intent, UX, domain language: `product`
- GitHub lifecycle, CI, PR, release: `github`
- Software architecture, API, security, tests: `engineering`
- Data schema, migration, import, datasets: `data-management`
- Neon-specific database infrastructure: `neon`
- Vercel-specific hosting and previews: `vercel`
- Recurring checks, research, monitoring: `automation`
- Outreach and launch: `promotion`

When several apply, coordinate without duplicating responsibility. A vendor-specific skill is optional when that vendor is absent. Use external maintained skills as supplements after checking provenance, version, license and fit. If a tool is unavailable, use a legitimate alternative or state the blocker; never simulate success.

## Definition of done

Acceptance criteria satisfied; relevant tests and docs updated; security/data effects reviewed; deployment/preview status honestly reported; evidence and outstanding risks recorded in the PR. Do not demand irrelevant rituals for trivial changes.
