---
name: self-review
description: The pass before anyone else looks at UI work — usability walked in the browser, type crimes (dashes, quotes, orphans), design-system drift, a confident handover, and the pre-review checklist (NN/g, 5 Common Mistakes Junior Designers Make)
---

Self-review `$ARGUMENTS`. If nothing is named, review the uncommitted changes
(`git diff` and `git status`). Read `.claude/rules/self-review.md` first.

1. **Usable first.** Name the task the change serves. Walk it in the browser
   against a live API (`/run`, or the Chrome tools), with the mouse and then
   the keyboard, through loading, empty, error and permission denied. If it
   cannot be run, say so and continue from the code.
2. **Type crimes.** Read every new or changed user-facing string in the diff
   and check:
   - an en dash in ranges, an em dash only for empty cells, and a hyphen only in words
   - one-character ellipses
   - typographic quotes in sentences, and no contractions if the voice avoids them
   - balanced or pretty text wrapping against orphans
   - locale-correct numbers, units spaced, and percent not spaced
   - sentence case, full stops on sentences only, and spelling consistent with the existing copy files
3. **Inside the system.** Search the diff for hex values, arbitrary values,
   default greys, card shadows, native controls the system replaces, new icon
   imports, and one-off components that duplicate a shared one.
4. **Housekeeping.** Stray debug logging, commented-out code, unexplained
   TODOs, and fragile relative imports.
5. **Checks.** Run the project's lint, typecheck and build.
6. **Handover.** Write the summary as the rule's Rule 4 asks: the decision and
   why (with its source), the alternatives that lost, and what was not checked.

Fix what is plainly a mistake (type crimes, drift, housekeeping) and list each
fix. Anything that is a design decision is reported, not changed. End with the
Rule 5 checklist, each item ticked or marked not done.
