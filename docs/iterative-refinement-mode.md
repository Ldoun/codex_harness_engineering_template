# Iterative Refinement Mode

This repo supports an opt-in refinement loop for broad goals that benefit from repeated planning and evaluation.

## What It Is For
Use it for goals like:
- refine the mobile web UI
- improve a broader checkout flow
- rework a UX surface against a rubric

Do not use it for ordinary implementation, bug fixes, or narrowly scoped tasks that should stay on the default spec workflow.

## How To Trigger It
Ask Codex explicitly, for example:

```text
$iterative-refinement-loop refine the mobile web UI for checkout. Use a 3-iteration budget. Focus the rubric on hierarchy, spacing, tap comfort, state clarity, and consistency. Stop when hard gates pass and the rubric average is at least 4.2/5.
```

The loop will not start implicitly for normal implementation requests.
For UI or UX loops, start by running `$visual-input` to capture the current or target visual reference and record the resulting artifact path in the iterative spec.

## Files Added For The Loop
- `docs/specs/_iterative-template.md`
- `.agents/skills/iterative-refinement-loop/`
- `.agents/skills/visual-input/`
- `artifacts/loops/README.md`
- `artifacts/visual-input/README.md`
- `scripts/evals/README.md`

## Closeout Behavior
Iterative work should remain in loop mode until the active spec sets:

```text
Loop Status: ready-for-final-validation
```

At that point the repo's normal validation and closeout skills can take over.
