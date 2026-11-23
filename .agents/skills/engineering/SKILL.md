---
name: engineering
description: Design and deliver maintainable software architecture, APIs, tests, security, observability and operational reliability without imposing a stack.
---

# Engineering

## When to use
Implementation, architecture, frontend/backend, API, security, debugging, code quality, reliability or operations.

## Procedure
1. Inspect repository and active docs; infer current stack rather than imposing one. Select smallest maintainable design consistent with business invariants.
2. Specify boundaries, trust zones, component contracts, error handling and API schemas (OpenAPI for HTTP APIs where useful). Keep frontend/server/database concerns separated.
3. Implement with focused changes, safe dependency choices and compatible API/schema evolution. Coordinate migrations and datasets with `data-management`.
4. Validate on server, enforce authorization and least privilege, keep secrets server-side, consider abuse controls for public writes. Apply accessibility and responsive UX where relevant.
5. Test proportionally: unit, integration, API, browser/E2E for critical journeys, negative paths and regressions. Do not confuse typecheck/build with functional verification.
6. Maintain architecture, API, operations, Mermaid diagrams and ADRs in same PR when changed. Docs must reflect code, not imagined future features.
7. For rollout, consider logs/metrics, health checks, backups, feature flags, backward compatibility, incident diagnosis and rollback that preserves newer user data.
8. Report concrete evidence, untested surfaces and known risks; do not claim production health from deployment status alone.

## Definition of done
Observable acceptance criteria met, tests relevant and documented, no unreviewed data/security regression, operations and rollback considered as warranted.

## Boundaries
This skill does not own GitHub approval policy, provider provisioning or the reference-data import lifecycle. Use `github`, `neon`, `vercel` and `data-management` as needed.
