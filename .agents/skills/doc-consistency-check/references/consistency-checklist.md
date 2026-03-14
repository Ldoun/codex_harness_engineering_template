# Consistency Checklist

Use this checklist when reviewing `docs/product.md`, `docs/engineering.md`, `docs/plan.md`, `docs/spec-index.md` when present, and the active spec referenced by `docs/plan.md`.

## Document Contract

- `docs/product.md`: durable product intent
- `docs/engineering.md`: durable technical truth
- `docs/plan.md`: current execution state
- `docs/spec-index.md`: lightweight visibility and lifecycle index for all specs
- active spec: scoped working contract for the current non-trivial change

## Review Targets

- Read `AGENTS.md` first to confirm the repo's document roles.
- Read the active spec path from `docs/plan.md`.
- Read `docs/spec-index.md` when it exists.
- Ignore `docs/specs/_template.md` as a review target.
- If no active spec is named, record that as a finding and continue.

## Issue Classes

- Role violations: content lives in the wrong document.
- Contradictions: two docs disagree on the same fact or expectation.
- Linkage drift: plan objective, active spec, and next step do not point at the same work.
- Incompleteness: unresolved placeholder text or starter text remains in real project docs.

## Checks

- Product goals or non-goals do not conflict with active spec scope.
- Product workflows and success criteria still match the current implementation direction.
- Engineering constraints, interfaces, environment assumptions, and validation commands do not conflict with the active spec.
- Stable architecture has not leaked into the active spec.
- Feature-scoped behavior has not leaked into `docs/engineering.md`.
- `docs/plan.md` objective, active spec, next step, and blockers describe the same current work unit.
- `docs/spec-index.md` status matches the corresponding spec file status.
- The active spec in `docs/plan.md` is present in `docs/spec-index.md` and is not marked `complete` or `removed`.
- `docs/spec-index.md` does not imply multiple active specs.
- A `complete` or `removed` spec is not still named as active in `docs/plan.md`.
- `docs/plan.md` does not contain roadmap or task-journal content.
- Real project docs do not still rely on unresolved template placeholders.

## Repair Boundaries

- Fix clear alignment issues directly when the task context calls for repair.
- Surface missing product or architecture decisions instead of inventing them.
- Prefer the smallest useful edit that restores consistency.
