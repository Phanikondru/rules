# Forms and selection — one rhythm, one "chosen" look

Applies to **every form** (sign in, change password, create/edit records, any
dialog with a field) and **every choosable thing** (dropdowns, multi-select,
filters, a row opened in a sheet). Sources: the project's design system / style
guide doc (e.g. `DESIGN.md`) sections on spacing, dropdowns, forms and
multi-select. NN/g:
[Website Forms Usability](https://www.nngroup.com/articles/web-form-design/) ·
[Reporting Errors in Forms](https://www.nngroup.com/articles/errors-forms-design-guidelines/) ·
[Placeholders Are Harmful](https://www.nngroup.com/articles/form-design-placeholders/) ·
[Marking Required Fields](https://www.nngroup.com/articles/required-fields/).

## Form spacing

The rule is Material 3's: **the space inside a group is always smaller than the
space around it**.

| Gap | Example | Between |
|---|---|---|
| 4 | small step | a field and its own label, hint or error (`control-size.md`) |
| 16 | medium step | one field and the next |
| 24 | large step | one group of fields and the next |

Use the steps in the style guide and nothing between them. **If a form feels
cramped, widen the gap between fields**, never the label gap.

**Space before a box.** Plain fields separated by space is the default. Add a
section heading, divider or card only when a group needs a title and its own
edge, never to make up for tight spacing. Two columns only when the fields are a
pair, such as start and end dates side by side, or latitude and longitude.

## Fields

- **Use the project's shared field components** (text field, text area, select /
  dropdown, multi-select, field layout). They carry the label, the control
  height, the error style and the password reveal. A native `<select>` is not
  used when the project has its own dropdown.
- **Every control has one height and the body type size**, set as a height and
  not built from padding. A native date input takes the same height.
- **A label is above its field**, medium weight. The placeholder is an
  example, never the label. Hiding the label is only for a filter bar.
- **Required-ness is visible before submit**: an asterisk beside the label.
  Where most fields are optional, mark the required ones. Where most are
  required, say "All fields are required unless marked optional" once at the
  top.
- **A placeholder never carries anything the person must remember** (NN/g:
  placeholders are harmful). It disappears on typing, is low contrast, and is
  mistaken for a filled value. Hints go under the field.
- **Set the input for the answer**: `type`, `inputMode`, `autoComplete`,
  `name`. A phone number gets `inputMode="tel"`, and sign-in fields get the
  browser's credential autocomplete.
- **Size the box to the answer.** A reason is one line, and a long free-text
  body is a text area.
- **Errors sit under the field that caused them**, say how to fix it, and stay
  until fixed. A form-level failure uses one shared form-error component. On a
  failed submit, **focus moves to the first invalid field**, and a long form
  also lists the problems at the top. Validate a field when the person leaves
  it, not on every keystroke, and never before they have typed.
- **Never clear what the person typed** on a failed submit.
- **Doubt warns, it does not refuse**: a value the system cannot verify but can
  doubt raises a warning panel and still saves.
- **Fields that stop being editable once a record exists** are replaced by a
  sunken panel with a caption saying why, and are never shown as a disabled
  input.
- **Validation rules come from the API.** The client may check shape (empty,
  length, format) for speed. It never owns a business rule.

## Choosing one

One dropdown pattern:

- **The chosen option has a tick on the right and a heavier label**, and no
  wash. The row under the pointer or keyboard takes a neutral hover tint.
- **It opens on the current choice.** A search field appears above the list
  after a threshold (e.g. eight options).
- `role="combobox"` on the trigger, `role="listbox"` on the list, and
  `role="option"` with `aria-selected` on each row. Full keyboard support.

## Choosing several

One multi-select pattern: a search box above a checkbox list, with removable
chips under the trigger, a count line, and **no "select all"**.

## Chosen rows and open records

- **The row opened in a sheet takes the soft accent, and its subject takes the
  accent.**
- **Status colours never mean chosen**, and the soft accent never means a
  status.
- **A focus ring is focus, not selection.**
- **Nothing is picked until the person picks it.** No default that commits a
  record on the person's behalf.

## Filters

- **Every applied filter is a removable chip.** The only exception is a lone
  text search in a narrow column, which carries a count line instead.
- **Clear all** is present when more than one filter is applied.
- **Filter state lives in the URL** where the page is shareable.

## Checklist

- [ ] Gaps follow the style guide, and the gap inside a group is smaller than the gap around it
- [ ] Shared field components used, every control one height and body size
- [ ] Labels above fields, required marked, input type and autocomplete set
- [ ] Errors under the field, persistent, and input kept on failure
- [ ] Doubt warns, fixed fields explain why, and no business rule in the client
- [ ] Choosing uses the one dropdown / multi-select pattern, with a second signal and ARIA state
- [ ] Applied filters are visible and removable
