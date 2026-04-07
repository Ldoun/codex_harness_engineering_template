# Frontend UX Refinement Checklist

Use this checklist when refining an existing UI.

## Before Editing
- Read the active spec.
- Read `docs/ux.md` and `docs/engineering.md`.
- Read the visual-input manifest if one exists.
- If the task is reference-driven and no manifest exists, run `$visual-input` first.

## Core Checks
- The primary task is obvious.
- Shared components and tokens are reused.
- The information hierarchy is stronger after the change.
- Loading, empty, error, disabled, focus, and selected states are handled when relevant.
- Mobile, tablet, and desktop behavior are checked.
- Accessibility regressions are not introduced.
- Visual validation evidence exists when the active spec requires it.

## Guardrails
- Preserve the existing design system unless the spec explicitly changes it.
- Favor clarity and consistency over novelty.
- Record remaining tradeoffs instead of hand-waving them away.
