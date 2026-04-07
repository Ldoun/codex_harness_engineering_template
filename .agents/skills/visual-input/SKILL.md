---
name: visual-input
description: Capture and normalize visual source-of-truth for UI implementation or refinement. Use when a task mentions screenshots, Figma, Storybook, a live route, an existing screen, "match this design", or "improve this UI". Do not use for backend-only work or open-ended art direction with no reference.
---

# Visual Input

Capture task-specific visual evidence before frontend implementation or refinement.
Use this skill to turn screenshots, Figma context, routes, stories, or existing screens into a normalized manifest that downstream skills can follow.

## Workflow
1. Read `AGENTS.md`, `docs/plan.md`, `docs/engineering.md`, `docs/ux.md`, and the active spec if one exists.
2. Determine the artifact directory:
   - iterative spec: `artifacts/loops/<spec-slug>/iter-<n>/reference/`
   - bounded spec: `artifacts/visual-input/<spec-slug>/`
3. Resolve visual sources in priority order:
   - exact Figma selection or frame
   - user-provided screenshots
   - repo-local Storybook story or app route
   - current live or deployed UI capture
4. If the source is Figma, capture both structured design context and a screenshot for the exact variant.
5. If the source is a route, story, or deployed UI, capture desktop and mobile screenshots in a real browser.
6. Write `manifest.md` using `references/manifest-template.md`.
7. Write `sources.json` with the raw reference list, source types, and chosen canonical source.
8. Save screenshots, design-context artifacts, and short notes on ambiguities or repo-convention overrides.
9. End with a brief summary of the source of truth, missing states, and any unresolved ambiguity.

## Rules
- Treat the manifest as capture, not design invention.
- Record ambiguity explicitly instead of guessing.
- If no visual source exists, stop and state `no visual source captured`.
- Repo-local UX and engineering contracts override ambiguous or conflicting visual details.

## Reference
Read `references/visual-input-checklist.md` for required inputs, blockers, source priority, and outputs.
