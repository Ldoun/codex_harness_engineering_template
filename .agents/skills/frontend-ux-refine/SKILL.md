---
name: frontend-ux-refine
description: Improve an existing web UI in place. Use for spacing, hierarchy, responsiveness, navigation clarity, state coverage, accessibility, and design-system consistency when a current screen or visual reference already exists. Do not use for greenfield art direction; use `visual-input` first when no manifest exists.
---

# Frontend UX Refine

Refine an existing UI without inventing a new art direction.

## Workflow
1. Read `docs/ux.md`, `docs/engineering.md`, `docs/plan.md`, and the active spec.
2. Read the visual-input manifest when present. If the task is reference-driven and no manifest exists, invoke `$visual-input` first.
3. Preserve shared components, tokens, typography, and interaction patterns unless the spec explicitly changes them.
4. Improve task clarity, spacing, hierarchy, navigation, accessibility, and state coverage before adding novelty.
5. Validate the result at the required breakpoints and note any remaining tradeoffs.

## Focus Areas
- information hierarchy and primary-action clarity
- spacing, alignment, and rhythm
- responsive behavior
- loading, empty, error, disabled, focus, selected, and success states when relevant
- keyboard access, semantic structure, and visible focus
- consistency with the existing design system

## Guardrails
- Do not invent a new visual language when refining an existing screen.
- Do not create feature-local component variants unless the spec promotes them into the shared system.
- Do not discard the manifest or spec because a prettier alternative seems tempting.
- Treat missing state coverage or poor responsiveness as more important than ornamental polish.

## Reference
Read `references/refinement-checklist.md` before closeout.
