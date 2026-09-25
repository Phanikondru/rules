---
name: forms
description: Build or review a form, dropdown, multi-select or filter — spacing, control height, labels, autocomplete, inline errors, doubt vs refusal, the one chosen look
---

The form or picker is `$ARGUMENTS`. Read
`.claude/rules/forms-and-selection.md`, the input checklist in
`.claude/rules/web-ux.md` (section 5), and the project's design system / style
guide doc (e.g. `DESIGN.md`) sections on spacing, forms, filters and
multi-select first.

1. **Every field earns its place.** The API decides what is required. Ask for
   nothing more, and pre-fill what the system knows, saying so.
2. **Spacing**: the gap inside a group is smaller than the gap around it. No box
   added to fix spacing.
3. **Shared controls only**: the project's text field, text area, dropdown /
   select, multi-select and field layout. Every control has the one height and
   body size. No native `<select>` where a project dropdown exists.
4. **Labels** above, required marked, and `type`, `inputMode`, `autoComplete`
   and `name` set for the answer.
5. **Errors** under their field, API field messages mapped to fields, a
   form-level failure in the shared form-error component, and typed input
   never cleared.
6. **Doubt warns** (the warning panel, save allowed). Fields fixed after
   creation are a sunken panel that says why.
7. **Choosing**: a tick and weight in the dropdown, multi-select with chips and
   a count line, full ARIA state and keyboard. Nothing picked for the person.
8. **Filters**: every applied value is a removable chip, with Clear all.
9. **Commit**: in the dialog footer, naming the outcome, with `busy` while
   saving. Enter submits.

When building, run the project's lint, typecheck and build. Report the
checklist from `forms-and-selection.md`, and say plainly if it has not been
tried from the keyboard in a browser.
