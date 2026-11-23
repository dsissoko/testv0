# GitHub and delivery setup checklist

This is an operator checklist, not a claim that settings have been applied.

- [ ] Set repository as template if desired; choose visibility and permissions.
- [ ] Prefer squash merges; enforce Conventional Commit-style PR titles; decide whether to disable merge/rebase alternatives.
- [ ] Protect `main` via rulesets/branch protection: PR required, required CI checks, appropriate reviews, no routine direct pushes.
- [ ] Enable deletion of merged head branches; choose least-privilege Actions token permissions.
- [ ] Configure issue and PR templates, labels, milestones, CODEOWNERS only when useful.
- [ ] Configure CI for selected stack; tests, build, docs and data checks as applicable.
- [ ] Configure Release Please **after** choosing versioning and release authorization model. Confirm exact trigger, permissions and behavior of release PR merge.
- [ ] Audit Vercel Git integration: pushing/merging main may automatically deploy production unless explicitly gated. Align technical settings with human release policy.
- [ ] Configure Neon/Vercel credentials per environment; prevent preview secrets/data from reaching production or browser bundles.
- [ ] Validate one PR end-to-end: isolated database, migration/import, preview URL, tests, human QA, cleanup.
- [ ] Define incident, backup, rollback, quotas and scheduled-job ownership.

Recommended workflow: issue → scope → implementation PR → CI + preview + QA → approved merge → approved release → prod data changes + deploy → smoke tests. Choose backward-compatible migrations and actual deploy order to avoid downtime.
