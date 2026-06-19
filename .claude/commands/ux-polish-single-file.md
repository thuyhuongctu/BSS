---
name: ux-polish-single-file
description: Workflow command scaffold for ux-polish-single-file in BSS.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /ux-polish-single-file

Use this workflow when working on **ux-polish-single-file** in `BSS`.

## Goal

Makes small UX improvements or micro-interaction changes, typically as focused edits to the main UI file.

## Common Files

- `index.html`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Edit index.html to adjust UI/UX details

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.