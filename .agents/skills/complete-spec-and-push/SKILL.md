---
name: complete-spec-and-push
description: Complete the active spec referenced by docs/plan.md by validating the current worktree, updating docs/spec-index.md and docs/plan.md, committing the active-spec changes, and pushing the current branch. Use when the user asks to finish or push a completed spec, or when active-spec implementation work is being concluded and is ready for closeout.
---

# Complete Spec And Push

## Overview

Validate the active spec, update spec tracking, isolate the active-spec changes, commit them, and push the current branch. Treat this as a closeout workflow, not as a raw reaction to a status flip.

## Workflow

1. Read `AGENTS.md`, `docs/plan.md`, `docs/spec-index.md`, and the active spec.
2. Require exactly one active spec in `docs/plan.md`. If there is no active spec, stop and report a blocker.
3. Read `references/closeout-checklist.md` and use it as the closeout contract.
4. Reuse `$validate-active-spec` as the gating validation flow.
5. Reuse `$doc-consistency-check` if plan/spec/spec-index linkage is inconsistent.
6. Require:
   - the active spec is complete or ready to be marked complete
   - validation is `satisfied`
   - plan, spec, and spec-index linkage is consistent
7. Update tracking docs before commit:
   - mark the spec `complete`
   - update `docs/spec-index.md`
   - remove or advance the active spec in `docs/plan.md`
   - if there is no next spec, leave `docs/plan.md` with no active spec and record why
8. Isolate the active-spec changes from unrelated worktree changes. If safe isolation is not possible, stop and report the issue instead of bundling unrelated work.
9. Derive the commit message from the active spec title or summary.
10. Commit the active-spec changes and push the current branch to `origin`.

## Closeout Rules

- Treat closeout as a task-end workflow, not as an automatic response to any `complete` status value.
- Use `docs/plan.md` as the source of the single active spec.
- Use `docs/spec-index.md` as lifecycle visibility, not as the source of active state.
- Do not push when validation is partial or failed, including when required TDD evidence or a documented TDD exception is missing.
- Do not push when the active spec is `_template.md`.
- Do not bundle unrelated code or unrelated docs into the closeout commit.
- Keep repair scope limited to active-spec code, tests, and tracking docs needed for closeout.

## Output

- State the closeout result clearly:
  - ready to push
  - blocked
  - pushed
- If blocked, explain whether the blocker is validation, linkage, or change isolation.
- If ready, update the tracking docs, commit with the active-spec-derived message, and push automatically.
- If no next spec is promoted, leave `docs/plan.md` without an active spec and make that explicit.

## Reference

Read `references/closeout-checklist.md` for the closeout gates, blockers, and sequencing rules.
