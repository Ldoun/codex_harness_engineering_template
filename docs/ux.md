# UX

Use this file for durable UX, interaction, accessibility, and visual-system truth.
Keep feature-specific visual decisions in specs.

## Experience Principles
- Optimize first for task clarity, hierarchy, and usability.
- Reuse shared tokens and components before adding variants.
- Novelty is allowed only when it clarifies the interface or is explicitly requested.

## Information Hierarchy
- Define the primary task for each surface.
- Keep one clear primary action or decision path per major screen.
- Secondary context should live in supporting regions, not compete with the primary workspace.

## Design System Contracts
- Canonical tokens and primitives win over one-off styling.
- Raw colors, spacing, or radii should be justified in the spec before they bypass the design system.
- Reference-driven UI work should preserve the design system unless the spec explicitly changes it.

## State Coverage Requirements
- Cover loading, empty, error, disabled, hover, focus, selected, and success states when relevant.
- Specs should call out which states are required for each surface.

## Responsive Baseline
- Verify mobile, tablet, and desktop layouts when a surface is responsive.
- No sticky or fixed control may obscure the primary action or key content.

## Accessibility Baseline
- Preserve semantic structure, labels, keyboard access, focus visibility, and sufficient contrast.
- Motion should be supportive, not required to understand the interface.

## Visual Validation Expectations
- When work is driven by screenshots, Figma, Storybook, or an existing screen, use `$visual-input` to capture a normalized visual manifest before implementation.
- Specs should record the canonical source of truth, required breakpoints, required states, and validation approach.
- Final validation should compare the implemented UI against the manifest and repo-local UX conventions, not only against generic aesthetics.

## Open Questions
- Durable UX questions that still affect future work:
