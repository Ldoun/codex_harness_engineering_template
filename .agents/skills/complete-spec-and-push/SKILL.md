---
name: complete-spec-and-push
description: Complete the active spec referenced by docs/plan.md by validating the current worktree, updating docs/spec-index.md and docs/plan.md, committing the active-spec changes, optionally splitting unrelated work into separate commits, and pushing the current branch. Use when the user asks to finish, wrap up, close out, ship, land, merge-ready, commit, or push completed active-spec work, or when active-spec implementation has clearly concluded and is ready for closeout.
---

# Complete Spec And Push

## Overview

Validate the active spec, update spec tracking, isolate the active-spec changes, commit them, optionally split unrelated work into separate commits, and push the current branch. Treat this as a closeout workflow, not as a raw reaction to a status flip.

## Trigger Guidance

Use this skill more aggressively for end-of-work requests around the active spec, including:

- explicit asks to `finish`, `wrap up`, `close out`, `ship`, `land`, `push`, `commit`, or make the work `merge-ready`
- requests to `complete the spec`, `finish the active spec`, or `push the current work`
- implementation turns where the active-spec work appears done, tests are green, and the user is signaling conclusion even if they did not literally say `push`

Do not treat this as permission to auto-push during normal implementation. The closeout gates below still apply.

## Workflow

1. Read `AGENTS.md`, `docs/plan.md`, `docs/spec-index.md`, and the active spec.
2. Require exactly one active spec in `docs/plan.md`. If there is no active spec, stop and report a blocker.
3. Read `references/closeout-checklist.md` and use it as the closeout contract.
4. Reuse `$validate-active-spec` as the gating validation flow.
5. Reuse `$doc-consistency-check` if plan/spec/spec-index linkage is inconsistent.
6. Require:
   - the active spec is complete or ready to be marked complete
   - validation is `satisfied`
   - if the active spec declares `Execution Mode: iterative-improvement`, its `Loop Status` is `ready-for-final-validation` or the spec is already complete
   - if the active spec will be removed from `docs/plan.md`, at least one relevant non-mock validation pass has succeeded with fixture discovery/source inputs disabled
   - plan, spec, and spec-index linkage is consistent
7. Update tracking docs before commit:
   - mark the spec `complete`
   - update `docs/spec-index.md`
   - remove or advance the active spec in `docs/plan.md`
   - if there is no next spec, leave `docs/plan.md` with no active spec and record why
8. Isolate the active-spec changes from unrelated worktree changes.
9. If unrelated changes remain and they can be understood, validated, and grouped safely, split them into additional logical commits instead of leaving them behind or bundling them into the active-spec commit.
10. If unrelated changes cannot be grouped safely into separate commits, stop and report the issue instead of guessing.
11. Derive the active-spec commit message from the active spec title or summary.
12. Commit the active-spec changes, then commit each unrelated logical group separately, and push the current branch to `origin`.

## Closeout Rules

- Treat closeout as a task-end workflow, not as an automatic response to any `complete` status value.
- Use `docs/plan.md` as the source of the single active spec.
- Use `docs/spec-index.md` as lifecycle visibility, not as the source of active state.
- Do not push when validation is partial or failed, including when required TDD evidence or a documented TDD exception is missing.
- Do not remove the active spec from `docs/plan.md` or push the closeout commit on fixture-only validation evidence.
- Do not push when the active spec is `_template.md`.
- Do not close out an iterative-improvement spec while `Loop Status` is still `idle`, `running`, or `blocked`.
- Do not bundle unrelated code or unrelated docs into the active-spec closeout commit.
- Unrelated changes may be pushed only in separate commits with their own clear scope and sufficient validation evidence for that scope.
- Prefer one logical group per unrelated commit; do not sweep all leftovers into a generic cleanup commit.
- Keep repair scope limited to active-spec code, tests, and tracking docs needed for closeout.

## Output

- State the closeout result clearly:
  - ready to push
  - blocked
  - pushed
- If blocked, explain whether the blocker is validation, linkage, or change isolation.
- If ready, update the tracking docs, commit the active spec with the active-spec-derived message, add any safe unrelated commits separately, and push automatically.
- If no next spec is promoted, leave `docs/plan.md` without an active spec and make that explicit.

## Reference

Read `references/closeout-checklist.md` for the closeout gates, blockers, and sequencing rules.
