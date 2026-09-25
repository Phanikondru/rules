---
name: recognition
description: Check a page or flow never makes the person remember what the screen could show — pick not type, context beside the action, visible filters and scope, labelled icons, no codes (NN/g, Recognition and Recall; heuristic 6)
---

The page, flow or component is `$ARGUMENTS`. Read
`.claude/rules/recognition-over-recall.md`, `.claude/rules/reading.md` §6 and
`.claude/rules/forms-and-selection.md` first. Then read the page, its forms,
its dialogs and its copy strings.

1. **Pick, do not type.** List every field whose answer is a known set. Each
   one is a dropdown or multi-select with search past eight options.
2. **Named, not numbered.** Every reference to a person, place or record uses
   the words users use. A lone id or code is a finding.
3. **Context beside the action.** For each button and dialog, is the value
   being acted on visible without scrolling or going back?
4. **Visible state.** Applied filters are chips, the scope is
   shown, the chosen row stays marked, and Back keeps filters, sort and page.
5. **Words with glyphs.** Every icon has its word, or is on the icon-only list
   with an `aria-label`. No numeric or letter command, and no generic tooltip.
6. **Protected recall.** Passwords and OTPs have the reveal control and the
   right `autocomplete`. No rule must be remembered to avoid an error.
7. **No unrequested recents.** Search history, recent records and saved views
   are not present unless the project's style guide already specifies them.

If the app can be run (`/run`, or the Chrome tools), do the main task without
notes and list every point where something had to be remembered. Otherwise say
the check was from the code.

Report each finding with `file:line`, what the person must remember, the rule
broken and its NN/g source, and the fix. Do not cite the April Fools' article
`recall-beats-recognition` as support. Do not change code unless asked. When
fixing, run the project's lint, typecheck and build, and say plainly that it
was not tried with real users.
