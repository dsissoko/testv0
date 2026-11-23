# Data management contract

**Status:** template.

## Data classes
1. **Schema**: versioned migrations and constraints.
2. **Reference data**: shared, reviewed, versioned domain datasets.
3. **Environment seed**: separate preview fixtures and explicitly approved production initial records.
4. **Runtime data**: user-generated/persistent records, never overwritten by routine imports.

## Proposed commands (adapt to stack)
`db:status`, `db:init`, `db:migrate`, `db:import`, `db:check`, each supporting explicit environment selection and dry-run where meaningful. Default to no writes. For destructive reset require separate confirmation.

## Import contract
Stable business keys, deterministic mapping, validation before mutation, transaction or compensating strategy, idempotency, import report and provenance when relevant. Verify import twice on disposable QA. Preview data must not contaminate production. Document migration and rollback compatibility.
