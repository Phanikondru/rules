---
name: targets
description: Check every clickable thing is big enough, far enough from its neighbours and close to what was used before it — hit area, labels as target, crowding, distance, menu order, touch on a tablet (NN/g, Fitts's Law and Touch Target Size)
---

The page, component or row is `$ARGUMENTS`. Read
`.claude/rules/target-size.md`, `.claude/rules/button-states.md`, and the
project's design system / style guide doc (e.g. `DESIGN.md`) sections on
buttons, forms, tables and breakpoints first. Then read every clickable control
in scope: buttons, icon buttons, row subjects, row actions, chip remove
controls, pager buttons, navigation items, menu items, checkbox rows and map
markers.

1. **Size.** Measure the hit area from the classes (height, width, padding),
   not the glyph. Anything under the project's floor is a finding. Controls in
   one row share a height.
2. **Visible target.** The hover background covers the whole hit area. An icon
   and its word, and a checkbox and its label, are one target.
3. **Primary.** The commit is a full-size button, not the smallest control on
   the screen.
4. **Spacing.** Adjacent targets have a gap. A destructive action that commits
   at once never sits beside a safe one.
5. **Distance.** The commit follows the last field. Row actions sit on the
   row. Dropdowns open from their trigger. Nothing shifts between repeated
   clicks.
6. **Menus.** The most used item is first, and the destructive one is last,
   set apart.
7. **Touch.** Anything visible is operable, nothing depends on hover, and no
   component bumps itself to a touch size on its own. If the screen is meant
   for a tablet, the missing coarse-pointer step is named.

If the app can be run (`/run`, or the Chrome tools), measure the hit areas
with `getBoundingClientRect()` at a desktop width, a tablet width and 200%
zoom. Otherwise say the check was from the code.

Report each finding with `file:line`, what the person experiences (a missed
click, a slow click, a wrong click), the rule broken and its NN/g source, and
the fix. Do not change code unless asked. A size change to a shared component
updates its style-guide entry in the same change. When fixing, run the
project's lint, typecheck and build, and say plainly whether it was tried on a
tablet.
