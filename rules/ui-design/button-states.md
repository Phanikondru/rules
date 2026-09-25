# Button states — what a control says about itself

Applies to **buttons and every other clickable control**: dialog buttons,
row actions, table subject links, tabs, navigation items, dropdown triggers,
chips and icon buttons. Source:
[Button States: Communicate Interaction](https://www.nngroup.com/articles/button-states-communicate-interaction/)
(Kelley Gordon, NN/g, 2025).

NN/g separates a button's **style** (primary, secondary, ghost, danger: how
important it is) from its **state** (whether and how it can be used right now).
The project's design system / style guide doc (e.g. `DESIGN.md`) sets the
styles. This file sets the states, and they must look the same on every style.

## The states on a desktop

| State | NN/g | Guidance |
|---|---|---|
| **Enabled** | High contrast, legible label | The variant's own colours |
| **Hover** | Signals it can be clicked | A brighter accent on the accent, a canvas tint on neutral controls, at the hover duration |
| **Pressed** | Visible within 100–150ms | A deeper accent. Immediate |
| **Focus** | A clear outline, not colour alone | A `focus-visible` ring with offset. Never removed without a replacement |
| **Loading** | Enabled look plus a spinner | A `loading` / `busy` prop. Clicks ignored |
| **Disabled** | Muted, lower contrast, not mistaken for live | `disabled` attribute, `cursor-not-allowed`, and a reason on screen |
| **Selected** | Not a button state. It belongs to choices | `forms-and-selection.md`, never a pressed look |

## Rules

1. **Every clickable control has all its states**: enabled, hover, focus,
   disabled where it can be, and busy where it starts work.
2. **Hover and pressed are immediate.** Colour only, at the hover duration. No
   scale, lift or shadow.
3. **Focus is visible on keyboard use** (`focus-visible`), on every control,
   including table subject links, navigation items and icon buttons.
   `outline-none` without a ring is a defect.
4. **Loading looks like the control that was clicked, still working.** The
   label stays, so the person can see what is running. A loading label never
   becomes a generic word that hides which action is running. Prefer the
   outcome in progress ("Allowing", "Closing") over "Working".
5. **Disabled must not look live.** It has lower contrast than any enabled
   control on the same screen, and a disabled primary never keeps a full accent
   fill. A filled button takes a muted disabled fill with a secondary-ink label,
   and an outlined one fades (e.g. `opacity-60`). It must still be readable.
6. **Say why a control is disabled**, beside it. Where no reason fits, leave it
   enabled and explain on click. A tooltip is not an explanation.
7. **Never disable to hide a failure.** A failed action is enabled again, with
   the error beside its cause.
8. **State is not colour alone.** Disabled also changes the cursor and the
   `disabled` attribute. Busy also shows a spinner and sets `aria-busy`.
9. **Style never stands in for state.** A secondary button is not a "disabled
   primary".
10. **A link is not a button, and the reverse.** A control that navigates is an
    `<a>` / `Link` (it opens in a new tab and shows its URL). A control that
    acts is a `<button type="button">`. A table subject that opens a sheet is a
    button styled as a link.
11. **After success, the screen says so** (`async-and-status.md`, rule 4).

## Checklist (every button or clickable change)

- [ ] Enabled, hover, focus, disabled and busy states all exist
- [ ] Hover and pressed feedback is immediate and colour-only
- [ ] `focus-visible` ring present on every control
- [ ] Loading keeps the label (or names the action), and ignores clicks
- [ ] Disabled has lower contrast than any live control, is not a full accent, and its reason is visible
- [ ] `disabled` / `aria-busy` / `aria-pressed` carry the state
- [ ] `<a>` navigates and `<button>` acts
