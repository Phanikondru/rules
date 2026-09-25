---
name: colour
description: Decide or review which colour something gets — contrast, status pairing, the 60/30/10 budget, one meaning per colour (NN/g colour guidance)
---

The colour question or screen is `$ARGUMENTS`. Read
`.claude/rules/colour-use.md`, `.claude/rules/colour-type-icons.md`, and the
colour section of the project's design system / style guide doc (e.g.
`DESIGN.md`) first. Values come from the theme config only.

1. **Which job is this colour doing?** Neutral, accent ("you can act on this"),
   status, or a chart series inside a chart. If none, the answer is a neutral
   and a word, not a new hue.
2. **One meaning everywhere.** Search for the token's other uses
   (e.g. `grep -rn "accent-soft" src`). If the new use gives it a second
   meaning, refuse it.
3. **Readable.** Text 4.5:1 and meaningful shapes 3:1, measured on the ground
   it actually sits on. On a dark navigation panel, a higher floor. Words take
   the dark status step, never a fill token. Links are the accent, never the
   info colour.
4. **Not colour alone.** The state also has a word. It must still read in
   greyscale (Chrome DevTools, Rendering, Emulate vision deficiencies).
5. **Budget.** For a screen, take a screenshot and check 60 / 30 / 10 by area.
   Fix a failure by demoting, never by adding a colour.
6. **No hex, no arbitrary colour, no default grey** in any component. If the
   theme config and the style guide disagree, say so. A shared value also
   changes in any sibling product's files.

Report each finding with the rule it breaks and the fix. When editing, run the
project's lint, typecheck and build. State that the colour has not been tried
with the real audience unless it has.
