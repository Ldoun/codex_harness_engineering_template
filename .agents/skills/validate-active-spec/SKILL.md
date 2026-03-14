---
name: validate-active-spec
description: Validate whether the current worktree changes satisfy the active spec referenced by docs/plan.md. Use when the user asks whether code changes satisfy the active spec, or before concluding implementation work tied to an active spec.
---

# Validate Active Spec

## Overview

Validate the current worktree against the active spec and return a verdict before making any repairs. Use this skill to check implementation coverage, missing validation, and out-of-scope changes relative to the active spec.

## Workflow

1. Read `AGENTS.md` to learn the repo workflow and document roles.
2. Read `docs/plan.md` and identify the active spec path.
3. If `docs/plan.md` does not name an active spec, report a blocker and stop instead of guessing.
4. Read the active spec and any validation guidance in `docs/engineering.md`.
5. Inspect the current worktree as the default change set: staged and unstaged changes plus the resulting repo state.
6. Compare the change set to the active spec's scope, behavior requirements, acceptance criteria, and test plan.
7. Run relevant validation commands from the active spec or `docs/engineering.md` when they exist and are feasible.
8. Return a verdict with evidence, missing validation, and concrete gaps tied to the active spec.
9. Repair clear code or test issues only when the task context calls for it.

## Validation Rules

- Treat the active spec as the implementation contract.
- Use the current worktree as the default change set.
- If there are no worktree changes, report that no default change set was found unless the user explicitly wants the whole checkout validated.
- Treat missing active spec linkage in `docs/plan.md` as a blocker, not as partial satisfaction.
- Distinguish failures from validation gaps:
  - unmet requirement or contradicted acceptance criterion = not satisfied
  - missing tests or missing evidence = partially satisfied
  - missing active spec path = blocker
- If doc or spec linkage is the blocker, point to `$doc-consistency-check` instead of rewriting docs here.
- Keep repair scope to code and tests only.

## Output

- Start with one verdict: `satisfied`, `partially satisfied`, or `not satisfied`.
- Support the verdict with:
  - evidence from the code and worktree
  - missing validation or unrun checks
  - concrete gaps against the active spec
- For review-only requests, stop after the verdict and findings unless the user asks for edits.
- For active implementation or closeout work, briefly state the verdict and then repair clear code or test issues when the path forward is clear.

## Reference

Read `references/validation-checklist.md` for the detailed validation checklist and failure classification.
