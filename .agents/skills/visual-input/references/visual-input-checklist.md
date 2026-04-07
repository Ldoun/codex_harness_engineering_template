# Visual Input Checklist

Use this checklist when capturing visual source of truth for UI work.

## Required Inputs
- `AGENTS.md`
- `docs/plan.md`
- `docs/engineering.md`
- `docs/ux.md`
- the active spec, or enough task context to create or revise one
- at least one candidate visual source, unless the result should explicitly record that none exists

## Supported Source Types
- exact Figma selection
- user-provided screenshots
- repo-local Storybook story or app route
- current live or deployed UI capture
- mixed sources

## Source Priority Order
1. exact Figma selection
2. user-provided screenshots
3. repo-local story or route
4. current live or deployed UI capture

## Required Outputs
- `manifest.md`
- `sources.json`
- at least one desktop capture
- at least one mobile capture
- notes on ambiguous details and repo-convention overrides

## Manifest Must Record
- canonical source of truth
- source list
- required states
- required breakpoints
- reusable components or tokens to preserve when known
- ambiguities, gaps, or conflicts across references

## Blockers
- no clear active spec and no clear task scope
- no accessible visual source for a reference-driven request
- conflicting references with no defensible canonical source
- inability to save artifacts to the expected path

If any blocker applies, stop and report it instead of inventing a visual source.
