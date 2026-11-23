---
name: data-management
description: Model domain data and run deterministic, versioned, environment-aware schema migrations, imports, fixtures and data-quality checks.
---

# Data management — provider agnostic

## When to use
MCD/ERD, schema change, database initialization, reference data, CSV/JSON/YAML ingestion, data correction, import/update or data lifecycle.

## Four data classes
- **Schema**: ordered, versioned migrations and constraints.
- **Reference datasets**: shared, reviewed, versioned, stable business keys.
- **Environment-specific seed**: disposable preview fixtures **versus** separately approved production initial records.
- **Runtime/user data**: durable records, never reset or overwritten by normal seed/import.

## Procedure
1. Define business entities, identity, relationships, cardinalities, ownership, constraints, uniqueness, lifecycle; document Mermaid ERD and data dictionary.
2. Separate migration, reference import, seed and runtime writes. Keep reference files in Git with schema/format versions, provenance where useful, and validation rules.
3. Provide stack-appropriate commands, e.g. `db:status`, `db:init`, `db:migrate`, `db:import`, `db:check`; use explicit `--env preview|production` (or named target), `--dry-run` default for risky writes, and `--apply` only with appropriate authorization.
4. On empty QA: migrate → reference dataset → QA fixtures → check counts, keys, constraints and API behavior. Repeat imports; verify stable IDs, no duplicates and no unintended changes.
5. For updates: compute planned changes, validate format/types/FKs/units/business invariants, report inserts/updates/deletes; apply atomically where possible, with audit/compensation and idempotency.
6. For production: verify target connection/branch, backups, permissions, approval, backward-compatible rollout order; migrate and import **approved reference/production data only**. Never import preview fixtures to production.
7. Require separate explicit confirmation for reset/truncate/drop, schema recreation or data loss; a normal import must not silently reset user-generated records.
8. Verify post-write data and live API, record migration version, dataset hash/revision, counts, execution and rollback/forward-fix strategy. Handle irreversible migrations explicitly.
9. Agentic extraction/interpretation is allowed upstream; **structural checks and writes must be deterministic**. Do not invent data to satisfy expected counts.

## Definition of done
Fresh environment reproducible; repeat import idempotent; data classes isolated; destructive changes gated; source files, checks and actual DB state reconcile.

## Boundaries
No Neon dependency. `neon` handles provider branches/roles; `engineering` handles API implementation; `github` handles delivery authorization.
