---
name: update_base
description: Refresh the active project instruction file from the repo-local base template while preserving Section 8 project-specific instructions. Use when ./.agents/templates/research-base.md changed or when the user wants to sync Sections 0–7 without rewriting project details.
---

This project skill mirrors the `update_base` research command.

If the user supplied extra text alongside this skill invocation, treat that text as the command argument.

You need to update the project’s active instruction file from the latest repo-local base template while keeping the project-specific content intact.

## Steps

1. Determine the repository root:
   - Prefer `git rev-parse --show-toplevel`.
   - If that fails, use the current working directory as `$REPO_ROOT`.
2. Read the latest base template from `$REPO_ROOT/.agents/templates/research-base.md`.
   - If the template is missing, stop and tell the user exactly which file is missing.
3. Detect which active instruction file exists:
   - Check `$REPO_ROOT/AGENTS.override.md`.
   - Then `$REPO_ROOT/AGENTS.md`.
   - Use the first one found as `$INSTRUCTION_FILE`.
4. If no active instruction file exists:
   - Copy the template to `$REPO_ROOT/AGENTS.md`.
   - Tell the user you created a new root instruction file from the template.
   - Stop unless the user also asked you to customize Section 8.
5. Read the current project file at `$INSTRUCTION_FILE`.
6. Extract everything starting from `## 8. Project Instructions` (inclusive) to the end of the file. This is the project-specific content that must be preserved **exactly as-is**.
   - If the current file does not contain `## 8. Project Instructions`, stop and tell the user the file cannot be updated safely.
7. Combine the files:
   - Take the template content up to (but **not** including) `## 8. Project Instructions`.
   - Append the extracted project-specific content from the current file.
8. Write the combined result back to `$INSTRUCTION_FILE`.
9. Show the user a brief summary of what changed. Example: “Updated Sections 0–7 from `./.agents/templates/research-base.md` and preserved your Section 8 project instructions.”
10. If the resulting file is unchanged, say so clearly and do not create a commit.
11. If the file changed, leave the edit in the working tree unless the user explicitly asked you to commit it. If the user did ask for a commit, use: `chore: update instruction file base template`.
