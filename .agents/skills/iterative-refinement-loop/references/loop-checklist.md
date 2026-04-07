# Iterative Refinement Loop Checklist

Use this checklist when the user explicitly requests a scored or iterative refinement loop.

## Required Inputs
- `AGENTS.md`
- `docs/plan.md`
- `docs/engineering.md`
- `docs/ux.md`
- the active iterative spec, or enough context to create one from `docs/specs/_iterative-template.md`
- a broad goal that benefits from repeated planning and evaluation

## Blockers
- The user did not explicitly request iterative refinement.
- There is no clear broad goal to refine.
- The loop has no evaluation contract, artifact path, or stop condition.
- The repo state or docs do not make it possible to identify a single active spec.
- A UI-focused loop has no baseline visual source of truth and no plan to capture one with `$visual-input`.

If any blocker applies, stop and ask for the missing decision instead of silently entering loop mode.

## Loop Contract
- Convert the goal into hard gates plus a rubric.
- Record artifact commands and artifact locations in the active iterative spec.
- Keep an iteration budget and explicit stop conditions.
- For UI loops, capture and record a visual-input manifest before the first scored pass.
- Update the iterative spec after each pass with hypothesis, evidence, score, and next step.
- Keep `docs/plan.md` as a pointer, not a loop log.

## Ready For Final Validation
Set `Loop Status: ready-for-final-validation` only when:
- the rubric threshold or stop condition has been met
- hard gates are green or any remaining gaps are explicitly documented
- the current best result is recorded in the iterative spec
- the next meaningful action is final validation rather than another planning pass
