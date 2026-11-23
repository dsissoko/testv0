---
name: automation
description: Design, authorize and operate recurring agentic tasks for monitoring, moderation, research, quality, promotion and reporting across available schedulers.
---

# Recurring agentic automation

## When to use
User requests a reminder, repeated check, periodic report, ongoing monitoring, conditional alert, moderation or discovery of opportunities. Also proactively suggest a recurring task when it adds meaningful ongoing value, without creating it silently.

## Task contract
Record **ID, purpose, owner, schedule/timezone, trigger, sources/tools, query/scope, expected output, allowed actions, forbidden actions, approval gates, failure behavior, deduplication, notification destination, retention, cost limits and last successful run**. Store only non-sensitive metadata in project docs; credentials stay in provider secrets.

## Procedure
1. Separate deterministic schedules/checks (e.g. GitHub Actions cron) from tasks requiring research/interpretation/connectors (agentic scheduler). Pick available runtime, not a specific vendor. Confirm it can access necessary integrations when unattended.
2. Specify whether task is read-only, proposes actions, or may execute bounded writes. **Scheduled execution does not inherit unrestricted interactive-agent permissions.**
3. Define safety: no unapproved public posts, emails, deletions or irreversible production writes. For moderation, report/flag first; any automatic action needs explicit policy, legal basis, audit and rollback/appeal path as applicable.
4. Set cadence, timezone, lookback window, state/cursor, dedupe, retries, timeouts, alert thresholds and budget. Avoid duplicate reports/actions on retries.
5. Create task **only after approval**, using an actually available scheduler; verify returned task ID and schedule. If unsupported, provide a runnable spec and state the limitation.
6. Test one run or dry-run when supported. Record evidence and errors; report results, not imagined execution.
7. Review usefulness periodically, pause noisy tasks, and provide a way to edit, disable or remove the schedule.

## Examples
- Daily moderation: inspect new public submissions, classify suspicious items, produce evidence-backed review queue; never silently delete without authorized rules.
- Weekly promotion discovery: find relevant public conversations/communities, assess fit and platform rules, prepare non-spammy suggestions; **never publish or contact automatically without approval**.
- Daily technical health: inspect logs/alerts, summarize actionable anomalies and open a proposed issue if authorized.
- Dependency watch: report relevant security or compatibility changes, no automatic production update without review.

## Boundaries
`promotion` owns messaging and campaigns; `engineering` owns monitoring semantics; `data-management` owns data checks; `github` owns GitHub changes. This skill owns the recurring task lifecycle.
