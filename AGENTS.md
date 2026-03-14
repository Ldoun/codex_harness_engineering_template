# AGENTS.md

Purpose: operational instructions for coding agents working in this repository.

This repository uses a conversation-first, spec-driven workflow.
Project documents live under `docs/` and are created or refined through conversation
with the user. Treat those documents as living artifacts, not boilerplate.

## Canonical document locations

- `docs/product.md` — product intent, goals, non-goals, users, success criteria
- `docs/engineering.md` — architecture, stack, constraints, interfaces, validation rules
- `docs/plan.md` — current roadmap, active tasks, status, next steps
- `docs/specs/*.md` — feature-level contracts and acceptance criteria

Keep all project planning and design documents under `docs/`.
Keep this file focused on agent behavior only.

## Core operating rules

1. For non-trivial work, read `docs/plan.md` first.
2. If there is an active feature spec, use it as the implementation contract.
3. If the necessary docs do not exist or are clearly incomplete, create or update them
   as part of the task.
4. Major product or architecture decisions must come from conversation with the user.
   Do not silently invent them.
5. Prefer small, explicit edits over broad rewrites.
6. Keep documentation concise and structured.
7. Prefer finishing one scoped task before starting another.

## How to use the docs

### `docs/product.md`
Use for:
- problem statement
- target users
- goals and non-goals
- user-facing outcomes
- success criteria

Do not put implementation details here.

### `docs/engineering.md`
Use for:
- architecture boundaries
- module responsibilities
- data model or API constraints
- approved dependencies or tools
- testing and validation policy

Do not put roadmap or task tracking here.

### `docs/plan.md`
Use for:
- current phase
- ordered tasks
- task status
- blockers
- next action

The agent may update this file as work progresses or as the plan is refined through conversation.
Keep it brief.

### `docs/specs/*.md`
Use for feature-level contracts.
Each spec should define:
- objective
- in scope / out of scope
- functional requirements
- acceptance criteria
- test plan

If a task is larger than a small bugfix, prefer creating a feature spec before implementing.

## Conflict handling

If documents conflict:
- do not guess
- surface the conflict clearly
- propose a minimal resolution
- ask the user to choose when the conflict changes product or architecture intent

## Planning behavior

Before larger edits:
- identify the active task in `docs/plan.md`
- identify the relevant spec in `docs/specs/`
- inspect the existing code and tests
- propose or perform the smallest useful next step

When appropriate, update `docs/plan.md` to reflect:
- completed tasks
- narrowed next steps
- newly discovered blockers

## Coding workflow

When working in the codebase:
- prefer `rg` / `rg --files` for search
- inspect existing code before creating new abstractions
- avoid unnecessary dependencies
- avoid broad refactors unless requested or clearly required
- run relevant tests before concluding work
- add tests for new behavior when appropriate

## Documentation style

Documentation should be:
- short
- explicit
- scannable
- easy to revise in conversation

Prefer bullets, checklists, and compact sections over long prose.

## Bootstrap rule

If `docs/product.md`, `docs/engineering.md`, or `docs/plan.md` are only skeletons,
use them as writable templates and replace placeholders through conversation with the user.
Do not preserve placeholder text once concrete decisions have been made.
