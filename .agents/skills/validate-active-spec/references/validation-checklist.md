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
- The active spec is in iterative mode and the caller is trying to use auto-validation as final closeout before `Loop Status: ready-for-final-validation`.

If any blocker applies, do not guess. Report the blocker and point to `$doc-consistency-check` when the problem is document linkage rather than code.

## Core Checks

- The changed behavior matches the active spec's behavior requirements.
- Acceptance criteria are covered by implementation or are clearly unmet.
- For non-trivial behavior changes, claimed behavior has relevant automated tests unless a TDD exception is explicitly documented.
- If TDD is skipped, the active spec or `docs/engineering.md` records the reason and the equivalent validation evidence required instead.
- Claimed behavior has the required tests or the documented replacement validation evidence.
- Relevant validation commands pass, or missing execution is reported as missing evidence.
- If the current validation is being used to support spec closeout, at least one relevant validation pass has succeeded without fixture-backed or other mock discovery/source inputs.
- For iterative-improvement specs, distinguish a mid-loop checkpoint from final closeout validation. Only treat it as closeout-ready when `Loop Status: ready-for-final-validation`.
- The worktree does not include meaningful out-of-scope changes relative to the active spec.
- The active spec's test plan is reflected in the code changes, tests, or reported validation gaps.

## Verdict Rules

- `satisfied`: requirements are met, TDD expectations are met or explicitly waived, and validation evidence is sufficient.
- `partially satisfied`: implementation may align, but tests, commands, TDD exception rationale, or other evidence are missing or incomplete.
- `not satisfied`: one or more requirements or acceptance criteria are clearly unmet, contradicted, or missing from the implementation.

## Repair Boundaries

- Repair code and tests only when the task context clearly calls for it.
- Do not rewrite docs or specs in this skill.
- Surface doc/spec linkage problems separately and point to `$doc-consistency-check`.
