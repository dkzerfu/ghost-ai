# Progress Tracker

Update this file whenever the current phase, active feature, or implementation state changes.

## Current Phase

- Foundation

## Current Goal

- 02 Editor: build navbar, project sidebar shell, and dialog pattern (see `context/feture-specs/02-editor.md`).

## Completed

- 01 Design System: shadcn/ui (base-nova) initialised; Button, Card, Dialog, Input, Tabs, Textarea, ScrollArea added unmodified; `lucide-react` installed; `lib/utils.ts` exports `cn()`; `globals.css` is dark-only with `ui-context.md` tokens mapped to shadcn variables; `<html class="dark">`.

## In Progress

- 02 Editor chrome:
  - [x] `components/editor/editor-navbar.tsx` (fixed-height, left/center/right, sidebar toggle with `PanelLeftOpen`/`PanelLeftClose`)
  - [x] `components/editor/project-sidebar.tsx` (floating, slide-in, `isOpen` prop, My Projects / Shared tabs with empty states, `New Project` button)
  - [x] `components/editor/editor-dialog.tsx` (title, description, footer pattern; no concrete dialogs yet)
  - [x] tsc + eslint pass

## Next Up

- Pick the next feature spec after 02 Editor.

## Open Questions

- Add unresolved product or implementation questions here.

## Architecture Decisions

- Add decisions that affect the system design or data model.

## Session Notes

- 02 Editor components are mounted via `components/editor/editor-shell.tsx` (client; owns sidebar state) in `app/editor/layout.tsx`, with a placeholder `app/editor/page.tsx`. Sidebar is positioned inside the shell's `relative` content area, below the navbar. `EditorDialog` is the dialog pattern; no concrete dialogs built. `ProjectSidebar` takes optional `onClose` so the header close button can be wired by the parent.

- `lib/utils.ts` re-exports `cn` from the shadcn `cn` npm package (what the CLI generates; generated `components/ui/*` import it directly). `next build` was not verified (timed out, likely Google Fonts fetch); `tsc` and eslint pass.
- `app/globals.css` had no dark theme tokens when 01 started (only `@import "tailwindcss"`); tokens from `ui-context.md` are being added alongside shadcn setup.
