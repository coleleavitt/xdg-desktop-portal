---
name: add-new-portal-implementation-using-futures
description: Workflow command scaffold for add-new-portal-implementation-using-futures in xdg-desktop-portal.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /add-new-portal-implementation-using-futures

Use this workflow when working on **add-new-portal-implementation-using-futures** in `xdg-desktop-portal`.

## Goal

Adds a new implementation of a portal component (such as Request or Session) that uses futures and fibers for async handling, including source/header files and build system updates.

## Common Files

- `desktop-portal/meson.build`
- `desktop-portal/xdp-*-dex.c`
- `desktop-portal/xdp-*-dex.h`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Create new .c and .h files for the component (e.g., xdp-request-dex.c/h, xdp-session-dex.c/h).
- Update desktop-portal/meson.build to include the new source files.
- Implement the async logic using futures/fibers in the new files.

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.