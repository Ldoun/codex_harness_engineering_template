---
name: validate-active-spec
description: Validate whether the current worktree satisfies the active spec referenced by docs/plan.md. Use when the user asks whether code changes satisfy the spec, whether the work is done, ready for closeout, ready to push, ready to ship, or when implementation work appears complete and no user decision is blocking the next step.
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
6. Compare the change set to the active spec's scope, behavior requirements, acceptance criteria, and test plan, including any documented TDD exception.
7. Run relevant validation commands from the active spec or `docs/engineering.md` when they exist and are feasible.
8. If the validation is being used to support closeout or removal of the active spec from `docs/plan.md`, require evidence that at least one relevant validation pass succeeded with fixture-backed or other mock discovery/source inputs disabled.
9. Return a verdict with evidence, missing validation, and concrete gaps tied to the active spec.
10. Repair clear code or test issues only when the task context calls for it.

## Trigger Guidance

Use this skill not only when the user explicitly says `$validate-active-spec`, but also when they ask things like:

- "Does this satisfy the spec?"
- "Are we done?"
- "Is this ready to push?"
- "Is this ready to ship?"
- "Can we close this out?"
- "Did we finish the active spec?"
- "Before pushing, verify this work."

Automatically trigger this skill when the implementation phase appears to be ending and the next step is validation or closeout, unless a material user decision is still needed before validation would be meaningful.

Do not wait for explicit user wording if:

- code changes for the active spec have been made
- implementation or repair work has concluded for the turn
- relevant validation can be run without further product or technical decisions

Do wait if:

- the user is still choosing between approaches
- a blocking product or architecture decision is unresolved
- implementation is only partially complete and the current turn is clearly still in the build phase

## Validation Rules

- Treat the active spec as the implementation contract.
- Use the current worktree as the default change set.
- If there are no worktree changes, report that no default change set was found unless the user explicitly wants the whole checkout validated.
- Treat missing active spec linkage in `docs/plan.md` as a blocker, not as partial satisfaction.
- For non-trivial behavior changes, expect relevant automated tests unless the active spec or `docs/engineering.md` explicitly records why TDD was skipped and what equivalent validation replaces it.
- If the active spec is about to be removed from `docs/plan.md` as part of closeout, require a passing non-mock validation run for the relevant workflow; fixture-only evidence is not enough.
- Distinguish failures from validation gaps:
  - unmet requirement or contradicted acceptance criterion = not satisfied
  - missing tests, missing evidence, missing non-mock closeout validation, or undocumented TDD exceptions = partially satisfied
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
