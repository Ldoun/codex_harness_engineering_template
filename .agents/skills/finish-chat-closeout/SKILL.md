---
name: finish-chat-closeout
description: Run the repo closeout sequence at the end of an implementation chat. Use when the user asks to finish, wrap up, close out, ship, or push current repo work; when the user says proceed or continue after implementation is complete; or whenever the active spec is still present and docs/plan.md shows that closeout is the next step, so Codex should chain $doc-consistency-check, $validate-active-spec, and $complete-spec-and-push before ending the task.
---

# Finish Chat Closeout

## Overview

Use this as a wrapper skill when the task is ending and the repo should go through the standard closeout path before the chat finishes.

## Workflow

1. Confirm the work is actually in a closeout phase. Treat it as closeout when any of these are true:
   - the user explicitly asks to finish, wrap up, close out, ship, merge, commit, or push
   - the user says proceed, continue, or go ahead after Codex has already established that implementation and validation are complete and only closeout remains
   - the active spec's remaining step in `docs/plan.md` is effectively closeout rather than more implementation
   - the current turn itself just finished implementation or validation, the active spec still exists, and the next sensible action is closeout
   Do not use this skill for mid-implementation status checks.
2. Run `$doc-consistency-check` first.
3. If doc consistency finds a clear repair that belongs to the current closeout, apply it. If it finds a blocker or unresolved decision, stop and report it.
4. Run `$validate-active-spec` second.
5. If validation is not `satisfied`, stop and report the validation gap instead of pushing ahead.
6. Run `$complete-spec-and-push` last only after the first two skills have cleared the path.

## Guardrails

- Treat this skill as an orchestrator. Do not duplicate the full instructions from the three underlying skills.
- Use the repo's active spec from `docs/plan.md`. If there is no active spec, stop and report the blocker.
- Prefer repo state over phrasing. If `docs/plan.md` says the next step is closeout, treat a bare `Proceed` or `Continue` as a closeout trigger.
- Do not require the user to say `finish` explicitly once Codex has already moved the work into a closeout-ready state.
- If the current turn completes implementation and validation and leaves `docs/plan.md` in a closeout state, run this skill before sending the final response unless the user explicitly asked not to commit or not to push.
- Respect the stop conditions from the underlying skills. If any step says the work is blocked, do not continue to the next one.
- Keep the final closeout response explicit about the status: doc consistency result, validation verdict, and whether push happened.
