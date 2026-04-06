# Engineering

Use this file for durable technical truth. Keep feature-specific behavior in specs.

## System Boundary

- Repository or system boundary:
- External systems or dependencies touched:

## Interfaces and Contracts

- Primary interfaces:
- Input and output contracts:
- Failure, timeout, or retry expectations:

## Environment and Dependencies

- Languages, frameworks, and tools:
- Required environment assumptions:
- Shared dependencies or services:

## Harness Strategy

- Fixture or test-data approach:
- Observability or debugging expectations:
- Validation commands:
- Default testing approach for non-trivial behavior changes:
- When automation is impractical, acceptable replacement validation:
- For iterative refinement specs, define the eval contract in the active spec with hard gates, rubric criteria, artifact commands, artifact locations, and an iteration budget.
- Prefer artifact directories under `artifacts/loops/<spec-slug>/iter-<n>/` for screenshots, traces, and score files produced by a refinement loop.
- Keep baseline or current-best references in the active iterative spec rather than `docs/plan.md`.

## Constraints

- Technical constraints that shape implementation:
- Definition of done for engineering work:
- Manual verification is supplementary unless automated checks are genuinely impractical.
- Done means the behavior is implemented, relevant tests or equivalent documented validation exist, and the required validation commands pass.

## Open Questions

- Only unresolved technical questions that still affect implementation:
