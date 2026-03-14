# Closeout Checklist

Use this checklist when finishing the active spec, committing the active-spec changes, and pushing the current branch.

## Required Inputs

- `AGENTS.md`
- `docs/plan.md`
- `docs/spec-index.md`
- the active spec named by `docs/plan.md`
- the current worktree
- the validation result from `$validate-active-spec`

## Blockers

- `docs/plan.md` does not name exactly one active spec.
- The active spec does not exist.
- The active spec is `_template.md`.
- The active spec is not complete and is not ready to be marked complete.
- `$validate-active-spec` does not return `satisfied`.
- The active spec lacks required TDD evidence or a documented TDD exception, causing `$validate-active-spec` to remain below `satisfied`.
- Plan, spec, and spec-index linkage is inconsistent and cannot be repaired cleanly.
- Active-spec changes cannot be isolated safely from unrelated worktree changes.

If any blocker applies, stop and report it. Use `$doc-consistency-check` when the blocker is linkage rather than code.

## Closeout Sequence

1. Confirm the active spec and validation result.
2. Repair plan/spec/spec-index linkage if needed.
3. Mark the active spec `complete`.
4. Update `docs/spec-index.md` to match the completed spec.
5. Remove or advance the active spec in `docs/plan.md`.
6. Isolate the active-spec changes.
7. Generate the commit message from the active spec title or summary.
8. Commit the isolated changes.
9. Push the current branch to `origin`.

## Commit Scope

- Commit only the active-spec changes and required closeout doc updates.
- Do not bundle unrelated worktree changes.
- If isolation is not safe, stop instead of guessing.

## Success Conditions

- The active spec is complete.
- `docs/spec-index.md` reflects the completed state.
- `docs/plan.md` no longer points at a completed spec.
- The commit maps clearly to the completed spec.
- The branch is pushed successfully.
