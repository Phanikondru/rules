---
name: interactions
description: Review pointer, keyboard and overlay behaviour — hover-only actions, focus order and trapping, Escape, dialogs vs sheets, Cancel vs Close, accidental dismissal, confirmations, where alerts go (NN/g)
---

The page, component or interaction is `$ARGUMENTS`. Read
`.claude/rules/interactions.md` and the project's style guide sections on
navigation, tabs, modals and side sheets first. Then read the code: the page,
the shared dialog and sheet components, and any `onKeyDown`, `onMouseEnter`,
`tabIndex`, `focus()` or portal it uses.

Walk each way the person can interact, with the mouse and then with the
keyboard alone, and check:

1. **Visible equivalent**: every hover or shortcut action has a visible,
   keyboard-reachable control. No tooltip holds the only copy of anything.
2. **Honest shapes**: an underline is a link, a caret opens something, and
   anything clickable has a pointer cursor and a hover state.
3. **Keyboard**: Tab order follows reading order, there is no positive
   `tabIndex`, composite widgets use arrow keys, and focus is always visible.
4. **Overlays**:
   - focus moves in, is trapped, and returns to the opener
   - Escape closes only the topmost overlay
   - no two dialogs stacked, and a dialog over a sheet is the one allowed layer
   - a stray scrim click or Escape never loses typed input
5. **Cancel vs Close**: leaving keeps the work, and discarding is a labelled
   action.
6. **Confirmations**: only for costly actions, always the shared dialog, never
   `window.confirm` or `window.alert`.
7. **Feedback and alerts**: an immediate response to every click, problems
   beside their cause, and nothing that matters on a timer.
8. **Targets**: at least 24px for any icon button, and the project's control
   size otherwise. No drag-only action, nested menu or hover path to thread.
9. **URL state**: Back undoes the last drill-down, and links open in a new tab.

Report findings as: what happens, which rule it breaks (with its NN/g source),
and the fix. Do not change code unless asked. When fixing, run the project's
lint, typecheck and build, and say plainly if it has not been tried in a
browser.
