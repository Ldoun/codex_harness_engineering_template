# Eval Script Conventions

Place repo-local evaluation helpers for refinement loops here.

A useful pattern is one script per broad surface, for example:
- `scripts/evals/mobile-ui.sh`
- `scripts/evals/checkout-flow.sh`

Each script should ideally emit:
- hard-gate command results
- artifact output paths
- a structured score file that the iterative spec can reference

For UI loops, scripts may also consume visual-input artifacts or produce screenshot-comparison outputs referenced by the active spec.
