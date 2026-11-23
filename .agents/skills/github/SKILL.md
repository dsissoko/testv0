---
name: github
description: Manage GitHub product delivery, issues, milestones, PRs, CI, release governance and orchestration of preview environments.
---

# GitHub delivery

## When to use
GitHub issue, roadmap/milestone, branch, PR, Actions, release, CI/CD or delivery coordination. This skill owns GitHub orchestration; `neon` and `vercel` own provider-specific operations.

## Procedure
1. Inspect actual repository state: branch, issues, milestones, PRs, CI, permissions and settings. Never rely on remembered state.
2. Determine authorization phase: **issue discussion → PR scoping → PR implementation → merge approval → release approval**. Stay within the requested phase.
3. For issues, search duplicates, capture user outcome and acceptance criteria; update/create only with approval. Milestones describe product deliverables, not automatically versions.
4. For PR scoping, list included/excluded issues, risks, dependencies, acceptance, tests and rollout. One PR can address many issues; one issue can span PRs.
5. On approved implementation, branch from current main, use Conventional Commits and appropriately scoped commits, create PR. Use `Refs #N` for partial, `Closes #N` only when complete.
6. Run relevant CI checks: lint/types/tests/build/docs/data. Verify actual statuses and failed steps; do not invent results.
7. For webapp PRs, coordinate Vercel preview and Neon PR-specific branch. Ensure preview connects to **its own** database; run migrations, approved fixtures, HTTP and UI QA. CI green, preview READY and functional QA are distinct.
8. Merge only after explicit approval and checks. No direct main pushes. Verify branch protections, squash settings, token permissions, auto-delete, secrets.
9. For releases, choose SemVer + Release Please if suitable. Confirm whether release-please runs on push/main, workflow_dispatch or release PR merge; **no assumed relationship** between milestones and SemVer. A release PR, tag and production deployment are distinct actions.
10. Inspect Vercel's real Git integration: a main merge may auto-deploy regardless of written policy. Configure gates with approval before promising merge != deploy. Post-release verify smoke tests, migration/data status and rollback plan.

## Definition of done
Correct phase honored, GitHub links and checks verified, approvals respected, release/deployment state stated precisely. Never merge/publish merely because CI passes.

## External resources
GitHub Actions and Release Please official docs; GitHub Awesome Copilot skills can supplement this skill after provenance/version review.
