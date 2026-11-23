---
name: neon
description: Operate Neon PostgreSQL projects, branches, roles and PR-isolated databases while delegating generic migrations/import rules to data-management.
---

# Neon PostgreSQL

## When to use
Only if Neon is the chosen database provider and an authorized Neon integration/CLI is available.

## Procedure
1. Inspect actual project, region, database, branches, quotas, roles, permissions and connectivity. Never infer credentials or target from docs alone.
2. Identify protected production branch and QA strategy. Prefer **one PR → one isolated Neon branch** for relevant application changes, with stable PR-to-branch mapping and cleanup on PR close.
3. Choose branch mode deliberately: copy-on-write may expose production personal/sensitive data to previews. Prefer schema-only or sanitized/approved datasets where appropriate; enforce isolation, retention and access controls.
4. Create branch and credentials with least privilege; separate migration/import role from runtime role. Never expose PostgreSQL secrets to browser/public env variables or logs.
5. Coordinate `data-management` migration, reference import, preview fixtures and checks; confirm exact branch before any write.
6. Connect Vercel preview to **that PR's branch**, not one shared preview database URL. Validate mapping and actual API queries; handle race/cleanup, provider quotas and branch lifecycle.
7. For production rollout, obtain approval, back up/branch if appropriate, apply compatible migrations/data changes, verify permissions and HTTP functionality. Neon branch restore alone may discard newer writes; plan reconciliation.
8. Report branch ID, target, migration state, checks and deletion/retention status; do not claim availability without verifying it.

## Boundaries
Use `data-management` for schema/data contracts, `vercel` for deployment, `github` for PR orchestration. Official Neon agent skills are optional supplemental implementation references, not mandatory dependencies.
