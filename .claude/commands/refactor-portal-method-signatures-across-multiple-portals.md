---
name: refactor-portal-method-signatures-across-multiple-portals
description: Workflow command scaffold for refactor-portal-method-signatures-across-multiple-portals in xdg-desktop-portal.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /refactor-portal-method-signatures-across-multiple-portals

Use this workflow when working on **refactor-portal-method-signatures-across-multiple-portals** in `xdg-desktop-portal`.

## Goal

Refactors the method signatures or interface usage for multiple portal implementations at once, often to support new async patterns or data structures.

## Common Files

- `desktop-portal/*.c`
- `desktop-portal/*.h`
- `shared/*.c`
- `shared/*.h`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Update several portal .c files to use the new method signature or interface.
- Update shared or core header/source files to support the new pattern.
- Update the corresponding header files if needed.

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.