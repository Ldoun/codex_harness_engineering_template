---
name: setup_research_plan
description: Set up or resume a research project in this repository. Use when Section 8 project instructions are still placeholders, when report.tex or TODO.md are missing, or when the user asks to resume the research workflow.
---

This project skill mirrors the `setup_research_plan` research command.

If the user supplied extra text alongside this skill invocation, treat that text as the command argument.

You are a research agent. This skill sets up and executes a research project.

## Repository root and instruction file

1. Determine the repository root:
   - Prefer `git rev-parse --show-toplevel`.
   - If that fails, use the current working directory as `$REPO_ROOT`.
2. Detect which project instruction file to use:
   - Check `$REPO_ROOT/AGENTS.override.md`.
   - Then check `$REPO_ROOT/AGENTS.md`.
   - Use the first one found as `$INSTRUCTION_FILE`.
3. If neither file exists:
   - If `$REPO_ROOT/.agents/templates/research-base.md` exists, copy it to `$REPO_ROOT/AGENTS.md` and use that as `$INSTRUCTION_FILE`.
   - Otherwise stop and tell the user that the repo-local template is missing.

Check the state of `$INSTRUCTION_FILE` to determine what to do.

### Detection logic

- If `$INSTRUCTION_FILE` exists **and** its `## 8. Project Instructions` section contains filled-in values (not just placeholders like `[Research objective]`) **and** `$REPO_ROOT/report.tex` exists, treat this as **RESUME**.
- If `$INSTRUCTION_FILE` exists and Section 8 is filled in, but `$REPO_ROOT/report.tex` does not exist yet, treat this as **PARTIAL SETUP**.
- If `$INSTRUCTION_FILE` exists but Section 8 still has placeholders, treat this as **FRESH START**.
- If `$REPO_ROOT/research_instructions.md` exists (older format), read it as backward-compatibility input and migrate its useful content into Section 8 before continuing.

## RESUME

This is a resuming session. The project is already in progress.

1. Read `$INSTRUCTION_FILE` (especially Section 8), `$REPO_ROOT/report.tex`, and `$REPO_ROOT/TODO.md`.
2. Run `git -C "$REPO_ROOT" log --oneline -20` to inspect recent experiment commits.
3. Run `git -C "$REPO_ROOT" status` to check for uncommitted changes.
4. Summarize the current state to the user:
   - Best result so far and which experiment achieved it.
   - What was tried last and whether it worked.
   - What is next (from `TODO.md` or the last experiment’s “Next steps”).
5. Ask the user whether they want to continue the planned direction or pivot.
6. Continue the autonomous experiment loop.

## PARTIAL SETUP

This repository already has project instructions, but the research tracking files are not fully initialized.

1. Read `$INSTRUCTION_FILE` Section 8 and confirm it is ready to use.
2. Read any existing `$REPO_ROOT/TODO.md`, `$REPO_ROOT/REVISION.md`, or other project notes if present.
3. Show the user a concise summary of the current project instructions.
4. Proceed with the initial baseline setup from the “Fresh start” section, without re-asking questions that are already answered.

## FRESH START

1. Read `$INSTRUCTION_FILE` Section 8 to confirm it still needs to be filled.
2. If `report.tex` exists but Section 8 is empty, read `report.tex` to recover context, then ask the user to confirm project instructions before continuing.
3. Otherwise proceed with interactive setup below.

### Interactive setup

Guide the user through filling in the Project Instructions section. Use any extra user text that accompanied the skill invocation to bootstrap Round 1 — skip questions already answered by that text.

#### Round 1 — Goal & context

Ask at most 2–3 questions:

- What is the **research goal**? What are you trying to improve? (skip if clear from the extra text)
- What is the **primary metric**? Which direction is better?
- What is the **current state of the codebase**? Do we already have training or evaluation code, or are we starting from scratch?

Wait for the user’s response before continuing.

#### Round 2 — Evaluation & constraints

Ask at most 2–3 questions:

- What is the **evaluation command**? Example: `uv run python evaluate.py --split test`
- What is the **current baseline performance**? (if known)
- Are there **fixed constraints**? Example: model size, quantization bits, max training time, or architecture constraints.
- What is the **target improvement**?

Wait for the user’s response before continuing.

#### Round 3 — Approach, scope & model size

Ask at most 2–3 questions:

- Any **specific approaches** you want tried?
- Any **papers or references** to follow?
- What is the **minimum scale** for drawing conclusions? Example: “>=1.5B parameters” — smaller models are debugging-only per Commandment VII.
- Any **files that are off-limits**?
- What is the **compute budget**: how many experiments, how long can this run, and how many GPUs are available?

Wait for the user’s response before continuing.

#### Round 4 — Generate & confirm

1. Fill in the Project Instructions section of `$INSTRUCTION_FILE` by replacing the placeholder content in Section 8 with the gathered information:

```markdown
## 8. Project Instructions

**Goal:** [filled from Round 1]

**Primary Metric:**
- Name: [metric name]
- Direction: [lower/higher is better]
- Eval command: `[exact command]`
- Baseline: [value or "TBD"]

**Fixed Constraints (protected by Commandment II):**
- [from Round 2]

**Minimum Decision Scale (Commandment VII):**
- [from Round 3, e.g. ">=1.5B parameters — models below this are debugging-only"]

**Approach Guidelines:**
- [from Round 3, ordered by priority]

**References:**
- [papers or links from Round 3]

**Compute Budget:**
- [from Round 3]

**Off-Limits Files:**
- [from Round 3]

**Notes:**
- [any additional context]
```

2. Show the filled-in Section 8 to the user for review.
3. Ask whether they want to modify anything.
4. Save the updated instruction file.

### Initial baseline setup

After Section 8 is ready:

1. Explore the repository structure (`ls -la "$REPO_ROOT"`, read key files, understand the architecture).
2. If GPU work is relevant and `nvidia-smi` is available, record the GPU model and VRAM.
3. If `pyproject.toml` exists, run `uv sync`. If it does not exist, note that dependency setup is project-specific and continue.
4. Run the baseline evaluation (**E000**) using the evaluation command from Section 8 and record the result.
5. Initialize tracking files if they do not exist:
   - `report.tex` with a full preamble (`amsmath`, `amsthm`, `booktabs`, `graphicx`, `tcolorbox` with a verification box, theorem environments), a title/date, an experiment log table with an `E000` entry, and a baseline subsection.
   - `TODO.md` with initial open questions.
   - `mkdir -p "$REPO_ROOT/scripts" "$REPO_ROOT/images"`.
6. Commit with message: `exp(E000): baseline measurement -- <metric>=<value>`.
7. Begin the autonomous experiment loop described in the research workflow.
