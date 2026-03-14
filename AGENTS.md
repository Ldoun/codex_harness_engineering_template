# AGENTS.md

## Repo Purpose

Describe the current repository and the harness it supports in 1-2 lines.

## Core Philosophy

- Keep each document focused on a single purpose.
- Prefer current truth over history.
- Use specs to drive non-trivial changes.
- Prefer small, explicit edits over broad rewrites.

## Document Roles

- `docs/product.md` stores durable product intent only.
- `docs/engineering.md` stores durable technical truth only.
- `docs/plan.md` stores the current execution state only.
- `docs/spec-index.md` stores the lightweight index of all specs and their lifecycle state.
- `docs/specs/*.md` store scoped working contracts for non-trivial changes.
- `docs/specs/_template.md` is the starting point for creating a new spec.
- Brief references across docs are fine, but keep the full version of a fact in one best-fit place.

## Default Codex Workflow

- Read `docs/plan.md` first for non-trivial work.
- If `docs/plan.md` points to a spec, use that spec as the implementation contract.
- If a task is non-trivial and no spec exists, create one from `docs/specs/_template.md` before broad implementation and register it in `docs/spec-index.md`.
- One spec should cover one coherent behavior change. Split independently implementable or independently verifiable behavior into separate specs.
- Keep only one active spec in `docs/plan.md`. Use `docs/spec-index.md` for broader spec visibility instead of listing queued or completed specs in `docs/plan.md`.
- Update docs when decisions become concrete, and remove stale placeholders or notes.
- Raise major product or architecture decisions through conversation instead of silently inventing them.

## Harness Engineering Defaults

- Put stable interfaces, shared constraints, environment assumptions, and validation commands in `docs/engineering.md`.
- Put feature-scoped behavior, acceptance criteria, fixture or test-data needs, and failure cases in the relevant spec.
- Keep `docs/plan.md` focused on the next work unit: objective, active spec, next step, blockers.
- Prefer verification that proves the harness works in practice, not just in isolated units.
