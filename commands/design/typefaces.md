---
name: typefaces
description: Check or decide typeface use — one family, hierarchy by weight, multi-script support, the 1Il test, and what a second face would need (NN/g, The Dos and Don'ts of Pairing Typefaces)
---

The page, component or proposal is `$ARGUMENTS`. Read
`.claude/rules/typefaces.md`, then the typography section of the project's
design system / style guide doc (e.g. `DESIGN.md`), the `@font-face` rules in
the global stylesheet, and the font family/size config in the theme.

1. **One family.** Search the change for any `font-family`, `font-serif`,
   `font-mono`, `@font-face` or inline font in components, charts and map
   labels. Only the project's family and the system sans-serif fallbacks may
   appear.
2. **Hierarchy.** Does each level differ by weight first, then size from the
   ramp? Flag a heading that differs only by size, a faked bold, or an italic
   used for emphasis.
3. **Weights.** Is every weight used one of those loaded? Would the browser
   synthesise anything?
4. **Scripts.** Is the string type checked in every supported script, and is
   line height still the token's? Say if it was not viewed.
5. **1Il test.** Where codes appear (permit, vehicle, phone, reference
   number), are they `tabular-nums`, at body size or larger, in a weight that
   keeps `1`, `I` and `l` apart?
6. **A proposed second face.** Run the six conditions in the rule's section 5
   and answer each one. If any is missing, the answer is no, and say which.
   Offer the nearest fix in the existing family: weight, size, grouping or
   spacing.

Report each finding with its source (the rule section or the NN/g guideline)
and a fix. If the app was not run to look at the type, say the check was from
the code.
