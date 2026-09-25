# Control size — one consistent geometry on every form

Applies to **every text field, dropdown trigger, date field, button, checkbox
row and the form around them**: sign-in, change password, dialogs, filter bars,
settings pages. The principle: pick one measured geometry, record it in the
project's design system / style guide doc (e.g. `DESIGN.md`), and make every
form measure the same. Base it on **one** reference product, measured in the
browser with `getBoundingClientRect()`. Mixing heights from several products is
how a form ends up looking assembled.

`target-size.md` decides the minimum hit area and spacing between targets.
This file fixes the geometry of a form, so every screen measures the same.

## Example geometry

The values below are examples of the shape of such a table. Replace them with
your project's tokens.

| Part | Example |
|---|---|
| Text field | 32px, 1px border, 8px side padding |
| Primary and secondary button | 32px |
| Label | about 13px, medium weight, above the field |
| Label to field | 4px |
| Field to next label | 16px |
| Last field to the commit | 24px |
| Commit to an option under it (e.g. "keep me signed in") | 16px |
| One-task form width (sign-in) | about 320px |
| Commit width on a one-column form | full width |
| Password reveal | inside the field, trailing edge |
| Checkbox row | box before the words, label wraps the box |

## Rules

1. **Every control is one height**, on the sign-in page as much as in a filter
   bar. Set it as a height, never built from padding.
2. **No second control height.** "It looks short" is fixed by the form's width
   and spacing, never by a taller box. A touch size belongs to a touch product,
   and a collapsed-navigation target is its own token.
3. **Label, small gap, field. Field, larger gap, next label.** The gap inside a
   field is always smaller than the gap between fields
   (`forms-and-selection.md`).
4. **Extra space before the commit**, so the button reads as the end of the
   form, not as another field.
5. **A one-task form is a narrow fixed width.** A wider column makes a compact
   field look thin. A dialog form takes the dialog's width.
6. **Options that follow the commit sit a step under it**: the checkbox and its
   words are one `<label>`, and any help is a help tip beside it, outside the
   label.
7. **Same kind, same size.** Every control in one form or bar is the same
   height and the same body type size (`visual-design.md` §3).
8. **Help that is not needed to act goes behind a help tip**, never as a
   standing line under a checkbox. It opens on hover and on keyboard focus,
   closes on Escape, and is read by a screen reader without opening. A reason
   a control is disabled, a rule, or an error is never only in a tooltip
   (`interactions.md`, rule 1).
9. **Measure, do not eyeball.** Compare `getBoundingClientRect()` heights and
   gaps against the table, in the browser, at a fixed desktop width.

## Deviating from the reference

If the reference product differs from the design system on a token (a corner
radius, say), record the difference and change it in the style guide and theme
config together, if at all. Never in a single component.

## Checklist (every form change)

- [ ] Every control measures the one height, and none is taller
- [ ] Label to field, field to field and last field to commit follow the recorded gaps
- [ ] A one-task form has its fixed width, with a full-width commit
- [ ] Options under the commit sit a step below it, with the label as the target
- [ ] Extra help sits in a help tip, reachable by keyboard, and holds nothing required
- [ ] Measured in the browser against the table
