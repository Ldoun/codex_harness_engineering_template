# AGENTS.md

## Repo Purpose
Template repository for harness-engineered Codex workflows.
It provides doc-driven planning, spec execution, closeout, iterative refinement, and reference-driven frontend UX skills.

## Core Philosophy
- Keep each document focused on a single purpose.
- Prefer current truth over history.
- Use specs to drive non-trivial changes.
- Prefer small, explicit edits over broad rewrites.

## Document Roles
- `docs/product.md` stores durable product intent only.
- `docs/engineering.md` stores durable technical truth only.
- `docs/ux.md` stores durable UX, interaction, accessibility, and visual-system truth only.
- `docs/plan.md` stores the current execution state only.
- `docs/spec-index.md` stores the lightweight index of all specs and their lifecycle state.
- `docs/specs/*.md` store scoped working contracts for non-trivial changes.
- `docs/specs/_template.md` is the starting point for creating a new bounded spec.
- `docs/specs/_iterative-template.md` is the starting point for explicit iterative-improvement work.
- Brief references across docs are fine, but keep the full version of a fact in one best-fit place.

## Default Codex Workflow
- Read `docs/plan.md` first for non-trivial work.
- If `docs/plan.md` points to a spec, use that spec as the implementation contract.
- If a task is non-trivial and no spec exists, create one from `docs/specs/_template.md` before broad implementation and register it in `docs/spec-index.md`.
- Prefer test-driven development for non-trivial behavior changes. When practical, write or update the relevant failing test before implementing the behavior.
- If TDD is skipped, make the reason explicit in the active spec and require equivalent validation evidence before closeout.
- One spec should cover one coherent behavior change. Split independently implementable or independently verifiable behavior into separate specs.
- Keep only one active spec in `docs/plan.md`. Use `docs/spec-index.md` for broader spec visibility instead of listing queued or completed specs in `docs/plan.md`.
- Update docs when decisions become concrete, and remove stale placeholders or notes.
- Raise major product or architecture decisions through conversation instead of silently inventing them.
- For frontend or UX work, read `docs/ux.md` and the active spec before implementation.
- For reference-driven UI work, invoke `$visual-input` before changing code when the task mentions screenshots, Figma, Storybook, existing screens, live routes, or requests to match or improve an existing UI.
- Treat the visual-input manifest as the task-specific visual source of truth. Repo-local UX and engineering contracts override ambiguous reference details.
- Use `frontend-design` for greenfield or exploratory art direction when no exact visual source of truth exists.
- Use `frontend-ux-refine` for improving existing UI while preserving the current design system, information hierarchy, and interaction model.
- Run `web-design-guidelines` before closeout on materially changed UI files.

## Opt-in Iterative Refinement Mode
- Never enter a scored or multi-iteration refinement loop unless the user explicitly invokes `$iterative-refinement-loop`, explicitly asks to run an iterative refinement loop, or explicitly asks to continue an already-active iterative loop.
- Routine implementation, bug fixes, and ordinary feature work must stay on the default workflow.
- Use iterative refinement mode for broad goals that need repeated planning against evidence, such as refining a mobile web UI, reworking UX flow quality, or improving a broader product surface rather than fixing one narrow defect.
- In iterative refinement mode, keep `docs/plan.md` lean: objective, active spec, next step, blockers only.
- Store rubric criteria, hard gates, artifact paths, iteration budget, scores, hypotheses, and iteration history in the active iterative spec instead of `docs/plan.md`.
- For UI or UX loops, capture a baseline with `$visual-input` before the first scored pass and store the reference path in the active iterative spec.
- Implement one milestone-sized hypothesis per iteration, then run the evaluation contract before planning the next pass.
- Do not treat an iterative spec as ready for normal closeout until it sets `Loop Status: ready-for-final-validation`.

## Harness Engineering Defaults
- Put shared interfaces, environment assumptions, reusable validation commands, and visual artifact conventions in `docs/engineering.md`.
- Put durable UX principles, design-system contracts, accessibility baselines, and visual review expectations in `docs/ux.md`.
- Put feature-scoped behavior, acceptance criteria, visual inputs, fixture or test-data needs, failure cases, and any TDD exception in the relevant spec.
- Keep `docs/plan.md` focused on the next work unit: objective, active spec, next step, blockers.
- Prefer verification that proves the harness works in practice, not just in isolated units.
