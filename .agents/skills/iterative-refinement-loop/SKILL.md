---
name: iterative-refinement-loop
description: Run an opt-in, scored refinement loop for broad goals such as refining a mobile web UI or improving a wider product surface. Use only when the user explicitly invokes this skill, explicitly asks for an iterative or scored refinement loop, or explicitly asks to continue an already-active iterative loop.
---

# Iterative Refinement Loop

## Overview
Use this skill for broad, eval-driven improvement work where Codex should repeatedly plan, implement, evaluate, and re-plan against a concrete rubric.
This is not the default implementation workflow.

## When to Use
Use this skill only when one of the following is true:
- the user explicitly invokes `$iterative-refinement-loop`
- the user explicitly asks to run an iterative refinement loop or scored loop
- the user explicitly asks to continue an already-active iterative loop

Do not use this skill for ordinary implementation, bug fixes, or narrowly scoped tasks that should follow the standard spec workflow.

## Workflow
1. Read `AGENTS.md`, `docs/plan.md`, `docs/engineering.md`, `docs/ux.md`, and the active spec if one exists.
2. If there is no active iterative spec, create one from `docs/specs/_iterative-template.md`, register it in `docs/spec-index.md`, and point `docs/plan.md` at it.
3. Rewrite the broad goal into an evaluation contract with:
   - hard gates
   - rubric criteria
   - artifact commands
   - artifact locations
   - a baseline or current-best reference
   - a visual-input manifest path when the loop is UI-driven
   - an iteration budget
   - stop conditions
4. If the loop targets UI or UX, run `$visual-input` before the first scored pass and whenever the visual source of truth changes materially. Record the manifest path under the active spec's evaluation contract.
5. Keep `docs/plan.md` lean. Put the loop history, hypotheses, scores, and artifact references in the active iterative spec.
6. When useful, spawn read-only audit subagents for exploration or critique, then choose one milestone-sized hypothesis for the next pass.
7. Implement only one milestone-sized improvement at a time.
8. Run the evaluation contract, save artifacts, and compare against the previous best or baseline.
9. Update the iterative spec with the iteration result, evidence, score change, and next step.
10. Repeat until the stop conditions are met, the iteration budget is exhausted, or progress stalls.
11. When the loop is truly ready for normal closeout, set `Loop Status: ready-for-final-validation` and hand off to `$validate-active-spec`.

## Guardrails
- This skill is explicit-only. Never auto-enter the loop from a normal implementation request.
- Broad goals still need bounded iterations. Respect the iteration budget and stop conditions.
- Keep one active spec in `docs/plan.md`.
- Do not turn `docs/plan.md` into a running journal.
- Do not auto-close or auto-push iterative work until final validation and any closeout workflow have cleared.
- Prefer milestone-level changes over endless micro-tweaks.

## Output
- State the current loop status clearly.
- Summarize the evaluation contract, current best score, latest hypothesis, and next step.
- Call out whether the loop is continuing, blocked, or ready for final validation.

## Reference
Read `references/loop-checklist.md` for the required inputs, blockers, and stop conditions.
