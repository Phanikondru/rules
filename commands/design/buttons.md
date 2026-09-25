---
name: buttons
description: Check a button or any clickable control shows its state — enabled, hover, pressed, focus, loading, disabled (and why) — without confusing style and state (NN/g button states)
---

The button, row or page is `$ARGUMENTS`. Read
`.claude/rules/button-states.md`, the button section of the project's design
system / style guide doc (e.g. `DESIGN.md`), and the shared button and dialog
components first. Then read every clickable control in scope: buttons, row
actions, subject links, tabs, navigation items, triggers, chips and icon
buttons.

For each control:

1. **States present**: enabled, hover, focus, disabled where it can be, and
   busy where it starts work.
2. **Hover and pressed**: immediate and colour-only.
3. **Focus**: a `focus-visible` ring. `outline-none` without a ring is a
   finding.
4. **Loading**: `loading` / `busy` passed and cleared in `finally`. The label or
   the action in progress stays visible, and a second click does nothing.
5. **Disabled**:
   - lower contrast than every live control on the screen
   - never a full accent fill
   - still readable
   - **the reason is visible** beside it, or the control stays enabled and
     explains on click
6. **Semantics**: `<a>` / `Link` navigates and `<button type="button">` acts.
   `aria-label` on icon-only controls, `aria-busy` / `aria-pressed` where they
   apply, and a target that meets the size floor.
7. **Style vs state**: no variant is used to mean a state. There is one primary
   on the screen.

Report each finding with `file:line`, what the person sees, the rule broken and
the fix. When fixing the shared button or dialog, update the style-guide
button entry in the same change, and run the project's lint, typecheck and
build.
