---
name: frontend-design
description: Create distinctive, production-grade frontend interfaces for greenfield or exploratory UI work when there is no exact screenshot, Figma, Storybook, or existing-screen source of truth. Use for new pages, components, or surfaces that need art direction. Do not use for reference-driven UI matching or in-place UX refinement; use `visual-input` first in those cases.
license: Complete terms in LICENSE.txt
---

# Frontend Design

Create distinctive, production-grade frontend interfaces that avoid generic AI aesthetics.
Implement real working code with high attention to hierarchy, clarity, and finish.

## Workflow
1. Read `docs/ux.md`, `docs/engineering.md`, `docs/plan.md`, and the active spec if one exists.
2. If a `visual-input` manifest exists for the active spec, treat it as the source of truth and do not invent a new art direction. Work inside that envelope.
3. When no exact reference exists, choose a clear design direction that fits the product, audience, and technical constraints.
4. Reuse repo-local components, tokens, and interaction primitives before inventing feature-local variants.
5. Implement working code and cover meaningful states and responsive behavior.
6. Validate the rendered result in a real browser at the spec breakpoints when possible.

## Design Thinking
Before coding, understand the context and commit to an intentional direction:
- **Purpose**: What problem does this interface solve? Who uses it?
- **Tone**: Choose a deliberate mode such as refined, playful, editorial, raw, or utilitarian.
- **Constraints**: Respect framework, performance, accessibility, and repo-system limits.
- **Differentiation**: Decide what makes the surface memorable without undermining clarity.

## Aesthetic Guidance
Focus on:
- **Typography**: Inherit repo fonts by default. Only introduce new type choices when the brief explicitly calls for rebranding or a one-off expressive surface.
- **Color & Theme**: Commit to a cohesive palette. Use variables or tokens for consistency.
- **Motion**: Use motion to clarify transitions, feedback, and hierarchy. Avoid ornamental animation that does not help the task.
- **Spatial Composition**: Be intentional about rhythm, grouping, and contrast. Novel structure is welcome when it improves comprehension.
- **Backgrounds & Visual Details**: Add atmosphere only when it suits the concept and does not create noise.

## Anti-Patterns
Avoid:
- generic AI gradients and stock premium-SaaS styling
- cookie-cutter dashboards and card mosaics without task hierarchy
- inventing a parallel design system for one feature
- ignoring the active spec's states, breakpoints, or manifest requirements
- decorative flourish that makes the product harder to use

## Quality Bar
The result should be:
- production-grade and functional
- visually deliberate rather than generic
- consistent with repo-local UX contracts
- clear at mobile and desktop breakpoints
