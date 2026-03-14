---
name: doc-consistency-check
description: Check and repair consistency across docs/product.md, docs/engineering.md, docs/plan.md, docs/spec-index.md when present, and the active spec referenced by docs/plan.md. Use when the user asks for a document consistency review or repair, or when creating or revising a spec and you need to align product, engineering, plan, and spec documents.
---

# Doc Consistency Check

## Overview

Check the repo's canonical docs for role violations, contradictions, linkage drift, and incompleteness. Start with findings, then repair only when the task context clearly calls for edits.

## Workflow

1. Read `AGENTS.md` to learn the repo's document roles and workflow.
2. Read `docs/plan.md` and identify the active spec path.
3. Read `docs/spec-index.md` when it exists.
4. Read `docs/product.md`, `docs/engineering.md`, `docs/plan.md`, and the active spec if one is named and is not `docs/specs/_template.md`.
5. Read `references/consistency-checklist.md` and use it as the review contract.
6. Report findings ordered by severity with file references.
7. Apply straightforward doc fixes only when the user asked for repair, or when the work is spec creation or spec revision and the required fix is clear.

## Review Rules

- Treat `docs/` as project truth and this skill as procedure.
- Ignore `docs/specs/_template.md` as a review target.
- If `docs/plan.md` does not name an active spec, record that as a finding and continue with the canonical docs instead of guessing.
- Treat `docs/plan.md` as the sole source of the active spec and `docs/spec-index.md` as the visibility/index layer for all specs.
- Treat placeholder or starter text in real project docs as incompleteness, not as a hard contradiction.
- Do not invent missing product or architecture decisions. Surface them as open questions.
- Prefer small alignment fixes over broad rewrites.

## Output

- For review-only requests, stop after findings unless the user asks for edits.
- For spec creation, spec revision, or explicit repair requests, briefly surface the findings and then repair straightforward inconsistencies.
- Focus on four issue classes:
  - role violations
  - contradictions
  - linkage drift
  - incompleteness

## Reference

Read `references/consistency-checklist.md` for the document contract and the specific checks to apply.
