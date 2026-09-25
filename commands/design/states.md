---
name: states
description: Check a page never goes quiet — busy controls, table skeletons, error panels with Try again, permission denied, results, polling and count refresh
---

The page or action is `$ARGUMENTS`. Read `.claude/rules/async-and-status.md`
and the style guide doc's section on the four states first. Then read the page,
its hooks, and every request it makes.

For each thing that takes time or can fail, check:

1. **Busy**: buttons get a loading state and dialogs a busy state, cleared in
   `finally`. Rows have their own busy flag.
2. **Waiting**: tables load with a skeleton at the real row shape, never a
   spinner. A long action names what is running.
3. **Unreachable API**:
   - each section shows its own error panel with Try again
   - existing data stays, with a note that it is as it was
   - typed input is kept
4. **Denied**: a 403 takes the permission notice, never the error panel, and
   the table is not drawn.
5. **Result**: the page states what happened, and the button named the
   outcome.
6. **Age line and Refresh**: follow the project's decision on "As of" lines and
   page-level Refresh buttons.
7. **Refresh**: counts refresh on the event, polling is only for things caused
   elsewhere, and no list being acted on is polled.
8. **Failure of a count**: that element is empty and the rest works.
9. **Every state exists**: empty (with the right glyph for its meaning),
   loading, error and permission denied, all designed.

Report each missing or wrong state with the rule it breaks and the fix. When
fixing, run the project's lint, typecheck and build, and say plainly if the
failure paths have not been tried against a stopped API.
