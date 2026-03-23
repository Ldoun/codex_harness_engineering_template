---
name: retro
description: Reflect on the current research session and propose instruction improvements. Use after a research session, after repeated workflow failures, or when the user wants to refine this repository's research guidance.
---

This project skill mirrors the `retro` research command.

If the user supplied extra text alongside this skill invocation, treat that text as the command argument.

You are reflecting on the current research session to identify improvements for the repository’s research instructions. This is a retrospective — not about assigning blame, but about making future research sessions better.

User feedback may be empty. If the invocation included extra text, treat that text as the user’s feedback.

## Step 1: Gather context

1. Determine the repository root:
   - Prefer `git rev-parse --show-toplevel`.
   - If that fails, use the current working directory as `$REPO_ROOT`.
2. Detect which project instruction file exists:
   - Check `$REPO_ROOT/AGENTS.override.md`.
   - Then `$REPO_ROOT/AGENTS.md`.
   - Use the first one found as `$INSTRUCTION_FILE`.
3. Read the following files if they exist:
   - `$REPO_ROOT/REVISION.md` — previous retrospective entries.
   - `$REPO_ROOT/report.tex` — experiment log, results, and analysis quality.
   - `$REPO_ROOT/TODO.md` — open items and deferred work.
   - `$INSTRUCTION_FILE` — the instructions governing the session, especially Section 8.
4. Run:
   - `git -C "$REPO_ROOT" log --oneline -30`
   - `git -C "$REPO_ROOT" diff --stat HEAD~5..HEAD 2>/dev/null || true`
5. Backward compatibility: if `$REPO_ROOT/research_instructions.md` exists, read it as supplementary context for the original research goal.

## Step 2: Commandment compliance

Review compliance with each of the 10 Commandments in Section 1 of the instruction file. For each one, assess **followed**, **partially followed**, or **violated**, and provide evidence.

Use this checklist:

| # | Commandment | What to assess |
|---|---|---|
| I | Never break a promise | Did the agent follow through on stated intentions? |
| II | Never manipulate evaluation | Were metrics, test sets, and constraints kept unchanged? |
| III | Never fabricate citations | Were bibliography entries verified? |
| IV | Complete all autonomous work | Were tasks left incomplete or reported too early? |
| V | Make it work before moving on | Were methods discarded due to implementation bugs? |
| VI | One variable per experiment | Were experiments properly isolated? |
| VII | Evaluate in tiers | Was the three-tier strategy followed? |
| VIII | Bound your expectations | Were theoretical bounds established before heuristics? |
| IX | Record everything | Are results tables present? Are failures documented? |
| X | Verify before claiming | Were verification scripts created for non-trivial math? |

Also check module compliance when applicable: **C1/C2** for compute-intensive work and **M1/M2** for mathematical work.

This table goes into the `REVISION.md` entry.

## Step 3: Analyze the session

Reflect on these additional dimensions:

### A. Workflow & process

- Did the experiment loop work well?
- Were there unnecessary steps or missing steps?
- Was iteration speed good, or did the agent waste time on unproductive paths?

### B. Report quality (`report.tex`)

- Is the report clear, well-structured, and useful as a persistent record?
- Are experiment entries detailed enough to reproduce results?
- Are analyses insightful or superficial?
- Are results tables properly formatted with clear columns?

### C. Git discipline

- Are commit messages descriptive and following the prescribed format?
- Is branching used effectively?
- Are commits atomic (one idea per commit)?

### D. Error handling & recovery

- Did the agent handle failures well (OOM, NaN, divergence)?
- Were failed experiments documented properly?
- Did the agent recover autonomously or get stuck?

### E. Communication & autonomy

- Did the agent ask for help at the right times (not too often, not too rarely)?
- Were results reported honestly, including negative results?

### F. Resource management

- Was GPU or compute used efficiently? (Relates to module C1.)
- Were long runs estimated and confirmed before starting?

### G. User-specific feedback

- Address the user’s extra feedback text directly. This is the highest-priority input.
- If the user pointed out something specific, propose a concrete instruction-file change for it.

## Step 4: Write to `REVISION.md`

Update `$REPO_ROOT/REVISION.md` following these rules.

### If `REVISION.md` does not exist

Create it with this structure:

```markdown
# Instruction File Revision Notes

Collected observations and improvement suggestions from research sessions.
Each retrospective adds entries; later entries may refine or supersede earlier ones.

---

## Revision 1 -- [DATE]

**Session context:** [Brief description of the research task and current state]

**User feedback:** [What the user said, or "None provided"]

### Commandment Compliance
| # | Commandment | Status | Evidence |
|---|-------------|--------|----------|
| I | Never break a promise | followed/partial/violated | [evidence] |
| ... | ... | ... | ... |

### Proposed Changes

#### [Section of instruction file, e.g. "Section 3: Experiment recording"]
- **Issue:** [What was suboptimal]
- **Suggestion:** [Concrete change to instruction file wording or rules]
- **Rationale:** [Why this would help]

### Things That Worked Well
- [Keep these — do not fix what is not broken]

### Open Questions
- [Things that need more sessions to evaluate]
```

### If `REVISION.md` already exists

1. Read the existing content carefully.
2. Add a new `## Revision N` section at the end of the file.
3. Reference previous revisions where relevant.
4. If a previous suggestion turned out to be wrong or insufficient, note that explicitly.
5. Do **not** delete or modify previous entries.
6. If the same issue appears again, escalate its priority and refine the suggestion.

## Step 5: Summarize to the user

After writing `REVISION.md`, give the user a concise summary:

1. Commandment-compliance overview (how many followed, partial, and violated).
2. The top 3 most impactful proposed changes.
3. Any patterns across multiple retrospectives, if applicable.
4. Ask whether they want to elaborate on any point or add more feedback.

## Additional guidance

- Be conservative. Do not propose removing rules that exist for good reason (Commandments, verification). Prefer clarifications or additions.
- Focus on high-leverage changes — small wording tweaks that would have prevented significant issues or materially improved output quality.
- Distinguish one-off incidents from recurring patterns. One-off issues may not warrant an instruction change; recurring patterns usually do.
