# AGENTS.md

## Repo Purpose

This repository is a compact template for Codex-driven harness engineering projects.
Use `docs/` as shared working memory that helps the user and Codex stay aligned.

## Core Philosophy

- Keep each document focused on a single purpose.
- Prefer current truth over history.
- Use specs to drive non-trivial changes.
- Prefer small, explicit edits over broad rewrites.

## Document Roles

- `docs/product.md` stores durable product intent only.
- `docs/engineering.md` stores durable technical truth only.
- `docs/plan.md` stores the current execution state only.
- `docs/specs/*.md` store scoped working contracts for non-trivial changes.
- Brief references across docs are fine, but keep the full version of a fact in one best-fit place.

## Default Codex Workflow

- Read `docs/plan.md` first for non-trivial work.
- If `docs/plan.md` points to a spec, use that spec as the implementation contract.
- If a task is non-trivial and no spec exists, create or refine one before broad implementation.
- Update docs when decisions become concrete, and remove stale placeholders or notes.
- Raise major product or architecture decisions through conversation instead of silently inventing them.

## Harness Engineering Defaults

- Put stable interfaces, shared constraints, environment assumptions, and validation commands in `docs/engineering.md`.
- Put feature-scoped behavior, acceptance criteria, fixture or test-data needs, and failure cases in the relevant spec.
- Keep `docs/plan.md` focused on the next work unit: objective, active spec, next step, blockers.
- Prefer verification that proves the harness works in practice, not just in isolated units.
