---
name: product
description: Define product vision, domain vocabulary, functional journeys, UX, acceptance criteria and outcome-oriented roadmap.
---

# Product discovery and specification

## When to use
New product, ambiguous requirement, UX decision, domain change, roadmap or feature acceptance.

## Procedure
1. Read active vision, domain, functional docs, roadmap and relevant GitHub issues; identify what is fact, hypothesis or undecided.
2. Clarify actors, pain points, measurable outcome, scope and non-goals. Ask only questions whose answers materially change implementation.
3. Model domain terms, business identities, lifecycle, invariants and examples **before** designing database tables or UI controls.
4. Describe user journeys, mobile/accessibility behavior, loading/empty/error states, privacy expectations and acceptance tests.
5. Organize roadmap into strategic pillars, coherent milestones and actionable issues. Avoid binding milestones to SemVer unless explicitly chosen.
6. Capture decisions in docs and ADRs when consequential; coordinate API/architecture with `engineering` and domain data with `data-management`.
7. During review, compare delivered behavior with acceptance criteria and actual UI, not only the code diff.

## Deliverables
Updated vision/domain/functional docs, concise roadmap, issue acceptance criteria and clear outstanding decisions. Avoid over-documenting trivial changes.

## Boundaries
Do not invent business facts or source-verification rules for arbitrary products. Domain-specific research or validation belongs to the project, not to this universal skill.
