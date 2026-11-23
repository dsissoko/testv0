---
name: vercel
description: Configure and verify Vercel previews, server-side environments, production releases, logs and rollback with explicit GitHub approval gates.
---

# Vercel hosting

## When to use
Only if Vercel is selected for hosting/deployments.

## Procedure
1. Inspect actual Vercel project, Git integration, build settings, environments, domains, deployment protection, quotas and connected credentials.
2. Configure environment variables by scope: Production vs Preview, server-only vs client-exposed. Never place database secrets in public build variables.
3. For PRs, create/find deployment preview and obtain actual URL and deployment SHA. Coordinate with `neon` to bind the correct PR-specific database; ensure the environment mapping is real, not a naming convention alone.
4. Verify build and deployment, then run HTTP smoke tests and relevant browser/E2E journeys. READY alone is not functional QA; capture URL, commit, DB branch, test evidence and logs.
5. Inspect default auto-deploy behavior: Git-connected `main` commonly deploys automatically. If human-controlled release is required, explicitly configure and test a compatible technical gate before promising no production deploy on merge.
6. Production publication requires approval and compatible schema/data rollout plan. Verify production alias, endpoints, logs, data checks and user-visible version; distinguish rollback of code from recovery of writes.
7. Monitor runtime errors, cost/quota and protection settings. Avoid destructive or billing changes without separate approval.

## Boundaries
`github` owns PR/release approvals, `neon` owns database branches, `data-management` owns migration/import.
