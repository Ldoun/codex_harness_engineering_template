# Validation Checklist

Use this checklist when validating whether the current worktree satisfies the active spec named by `docs/plan.md`.

## Required Inputs
- `AGENTS.md`
- `docs/plan.md`
- the active spec named by `docs/plan.md`
- relevant implementation files from the current worktree
- relevant validation commands from the active spec or `docs/engineering.md`

## Blockers
- `docs/plan.md` does not name an active spec.
- The named active spec does not exist.
- The active spec is `_template.md`.
- The active spec status or plan linkage makes validation impossible.

If any blocker applies, do not guess. Report the blocker and point to `$doc-consistency-check` when the problem is document linkage rather than code.

## Core Checks
- The changed behavior matches the active spec's behavior requirements.
- Acceptance criteria are covered by implementation or are clearly unmet.
- If the active spec changes UI, the implementation matches the spec's visual-input or UX requirements.
- For non-trivial behavior changes, claimed behavior has relevant automated tests unless a TDD exception is explicitly documented.
- If TDD is skipped, the active spec or `docs/engineering.md` records the reason and the equivalent validation evidence required instead.
- Claimed behavior has the required tests or the documented replacement validation evidence.
- Relevant validation commands pass, or missing execution is reported as missing evidence.
- If the active spec declares visual inputs, there is visual validation evidence against the manifest or named reference at the required breakpoints and relevant states.
- If the current validation is being used to support spec closeout, at least one relevant validation pass has succeeded without fixture-backed or other mock discovery or source inputs.
- The worktree does not include meaningful out-of-scope changes relative to the active spec.
- The active spec's test plan and visual-validation plan are reflected in the code changes, tests, or reported validation gaps.

## Verdict Rules
- `satisfied`: requirements are met, TDD expectations are met or explicitly waived, and validation evidence is sufficient.
- `partially satisfied`: implementation may align, but tests, commands, TDD exception rationale, visual evidence, or other evidence are missing or incomplete.
- `not satisfied`: one or more requirements or acceptance criteria are clearly unmet, contradicted, or missing from the implementation.

## Repair Boundaries
- Repair code and tests only when the task context clearly calls for it.
- Do not rewrite docs or specs in this skill.
- Surface doc or spec linkage problems separately and point to `$doc-consistency-check`.
