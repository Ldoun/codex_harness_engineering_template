# Engineering

Use this file for durable technical truth.
Keep feature-specific behavior in specs.

## System Boundary
- Repository or system boundary:
- External systems or dependencies touched:

## Interfaces and Contracts
- Primary interfaces:
- Input and output contracts:
- Failure, timeout, or retry expectations:
- Canonical UI component layer or package, when relevant:
- Canonical token source of truth, when relevant:

## Environment and Dependencies
- Languages, frameworks, and tools:
- Required environment assumptions:
- Shared dependencies or services:
- Browser automation tool or MCP server, when used for visual capture or validation:
- Figma or design-context integration, when used for reference-driven UI work:

## Harness Strategy
- Fixture or test-data approach:
- Observability or debugging expectations:
- Validation commands:
- Default testing approach for non-trivial behavior changes:
- When automation is impractical, acceptable replacement validation:
- For iterative refinement specs, define the eval contract in the active spec with hard gates, rubric criteria, artifact commands, artifact locations, and an iteration budget.
- Prefer artifact directories under `artifacts/loops/<spec-slug>/iter-<n>/` for screenshots, traces, and score files produced by a refinement loop.
- Prefer visual-input artifacts under `artifacts/visual-input/<spec-slug>/` for bounded UI work and under `artifacts/loops/<spec-slug>/iter-<n>/reference/` for iterative UI loops.
- Default visual breakpoints, unless the active spec says otherwise: `390`, `768`, and `1440` pixels wide.
- Minimum visual-input artifact set for reference-driven UI work:
  - `manifest.md`
  - `sources.json`
  - at least one desktop capture
  - at least one mobile capture
- Keep baseline or current-best references in the active iterative spec rather than `docs/plan.md`.

## Constraints
- Technical constraints that shape implementation:
- Definition of done for engineering work:
- Manual verification is supplementary unless automated checks are genuinely impractical.
- For UI work, done means the behavior is implemented, relevant state coverage exists, and either automated or documented visual validation exists when the spec declares visual inputs.

## Open Questions
- Only unresolved technical questions that still affect implementation:
