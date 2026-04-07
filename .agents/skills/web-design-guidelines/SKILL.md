---
name: web-design-guidelines
description: Review UI code against repo-local UX contracts first and fresh external web-interface guidelines second. Use when asked to review UI, audit design, check accessibility, review UX, or validate changed frontend files before closeout.
metadata:
  author: vercel
  version: "1.1.0"
  argument-hint:
---

# Web Design Guidelines Review

Review files for compliance with repo-local UX contracts and external web-interface guidelines.

## How It Works
1. Read `docs/ux.md`, `docs/engineering.md`, `docs/plan.md`, and the active spec if one exists.
2. If a `visual-input` manifest exists for the task, read it and treat it as the task-specific visual source of truth.
3. Fetch the latest external guidelines from the source URL below.
4. Read the specified files, or infer changed frontend files from the worktree when possible.
5. Review in this order:
   - blocking issues against the active spec, visual-input manifest, or repo-local UX contract
   - consistency drift against design-system, responsiveness, accessibility, or state-coverage expectations
   - external best-practice issues from the fetched guidelines
6. Output findings grouped as `blocking`, `consistency drift`, and `polish`, using terse `file:line` references where possible.

## Guidelines Source
Fetch fresh guidelines before each review:

```text
https://raw.githubusercontent.com/vercel-labs/web-interface-guidelines/main/command.md
```

Use WebFetch to retrieve the latest rules. The fetched content contains the external rules and review format guidance.

## Usage
When a user provides files or a file pattern:
1. Read repo-local UX and spec context first.
2. Fetch the external guidelines from the source URL above.
3. Read the specified files.
4. Apply repo-local rules first and the fetched guidelines second.
5. Output findings grouped by severity and drift class.

If no files are specified and changed frontend files cannot be inferred safely, ask the user which files to review.
