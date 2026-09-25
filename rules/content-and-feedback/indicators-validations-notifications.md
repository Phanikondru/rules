# Indicators, validations and notifications — the right message in the right form

Applies to **every message the product shows that is not the screen's main
content**: status pills, counts and badges, count lines, field errors, form
errors, warning panels, error panels, permission notices and dialogs. Source:
[Indicators, Validations, and Notifications: Pick the Correct Communication Option](https://www.nngroup.com/articles/indicators-validations-notifications/)
(Kim Flaherty, NN/g, 2024).

`voice.md` decides the words. `async-and-status.md` decides that the product
never goes quiet. This file decides **which kind of message a thing is, and so
which component carries it**. NN/g's point is that the wrong kind harms the
experience even when the words are right.

## The three kinds

| Kind | NN/g | What it is tied to | Needs action? |
|---|---|---|---|
| **Indicator** | Contextual, conditional, passive | A piece of content or a control | No |
| **Validation** | An error about the person's input | The field or form they just used | Yes, to clear it |
| **Notification** | A system event, not necessarily caused by the person | A place on the screen, or the whole app | Action-required: yes. Passive: no |

## Picking the kind

Ask in this order:

1. **Did the person's input cause it, and must they fix it?** Validation.
2. **Is it about one thing on the screen, and only true sometimes?**
   Indicator.
3. **Is it an event from the system?** Notification. Then ask whether the
   person must act soon (action-required) or not (passive).
4. **Is it a refusal to show something (403)?** Neither an error nor a
   validation. It gets its own permission notice.

## How each kind is built

Map each kind to one component in the project's design system and use only
that. A typical mapping:

| Kind | Component | Examples |
|---|---|---|
| Indicator | Status pill, nav count badge, tab count, count line, stat figure | "Waiting", "7" on a nav item, "3 of 82 reporting" |
| Validation, one field | The field's error state: error border and caption under the field | "Mobile number is required" |
| Validation, whole form | A form-level error under the form | "That password did not work." |
| Doubt, not refusal | A warning panel inside the form | A coordinate outside the expected region |
| Notification, action-required | A dialog when the app must have an answer; otherwise a warning panel with its button | "Remove this item?", a device limit notice |
| Notification, passive | The error panel with Try again, the result on the row | "Could not load staff.", a pill that changed |
| Not permitted | A permission notice | "You need permission to view complaints." |

**Decide explicitly whether the product has toasts.** The rules below assume it
does not (no toast or snackbar, and no `window.alert` or `window.confirm`),
because a missed toast can cost a person the one fact they needed. If the
project does allow toasts, restrict them to minor, passive results and never
use them for errors.

## Rules

### 1. Indicators sit on the thing and tell the truth

- **Beside what they describe**: a pill on its row, a count on its nav item or
  tab.
- **Shown only while true.** A tab whose count has not loaded shows no count,
  not a nought.
- **Refreshed by the event**, not only by navigation.
- **Never colour alone.** A pill has its word, and a badge carries a figure.
- **Passive means no pressure.** No pulsing or flashing (`motion.md`).
- **A count that resolves by itself is not a queue.** It belongs in a tile, not
  on the nav.

### 2. Validations say how to fix it, where the input is

- **Under the field that caused it**, via the field's error state. A problem
  with the whole form uses the form-level error under the form.
- **API validation messages are matched back to their field** and put into the
  words the form uses. The reader never sees a code field name.
- **Say what to do**, not only what is wrong.
- **It stays until fixed**, and what was typed is never cleared.
- **It is announced**: the form error is `role="alert"`, and the field links its
  error with `aria-describedby` and sets `aria-invalid`.
- **Never a toast, and never a dialog** for a validation.
- **Shape only in the client.** Anything beyond empty, length and format is the
  API's answer.

### 3. Action-required notifications interrupt only as much as needed

- **A condition the person should fix is a warning panel** in place, with its
  button inside it.
- **A dialog only when the app must have an answer**: a destructive or costly
  step, or a second ask ("Add it anyway").
- **A refusal is a dialog that says why**, not a disabled button with no
  reason.

### 4. Passive notifications persist, in place

- **In the content, where it applies**: a section's error panel inside that
  section.
- **Nothing on a timer.** A person who looked away misses a message that fades.
- **A result shows on the thing that changed** (the row, the count), not in a
  corner.

### 5. Error messages: NN/g's twelve, applied

From [Error-Message Guidelines](https://www.nngroup.com/articles/error-message-guidelines/)
(NN/g, 2023).

**Visibility**
- **Beside the source**: under the field, or inside the section that failed.
- **Noticeable and redundant**: error colour on text and border, plus the
  words. Never colour or motion alone.
- **Presented by severity**: a field problem goes inline, a failed section gets
  the error panel, and a blocked commit gets the form-level error. NN/g allows a
  toast for minor issues; where the project has no toasts, minor issues go
  inline instead.
- **Not premature**: validate a field when it is left, never before anything
  has been typed.

**Communication**
- **Human-readable**, with no codes and no code field names.
- **Precise**: never "An error occurred" when the cause is known.
- **Constructive**: say what to do next.
- **No blame**: avoid "invalid" and "illegal". "That date is after the end
  date", not "Invalid date".

**Efficiency**
- **Guard against likely mistakes** before they happen: for example a warning
  when coordinates look swapped, or when a new name nearly duplicates an
  existing one.
- **Keep the input.**
- **Offer the likely fix** where there is one ("Use the existing name?").
- **Explain the system briefly** only when it helps the fix.

**Total failure**: NN/g allows novelty when everything is down. Whether to use
it depends on the product's tone (`voice.md`); in a serious register, say
plainly what is down and what to do.

### 6. Do not mix the kinds

| Mistake | Why it fails | Instead |
|---|---|---|
| A field error in the form-level error | The person has to find which field | Under the field |
| An error as a toast | Gone before it is read (NN/g) | Form-level error, or under the field |
| A 403 as the danger panel | Reads as something broken | The permission notice |
| Information in a dialog | Interrupts for nothing | Text on the page |
| A status only as a coloured dot | Missed by colour-blind readers | A status pill with its word |
| A doubtful value blocked as an error | Stops the person recording something real | The warning panel, save allowed |
| A disabled button with no reason | Reads as broken | Enabled, with the reason given on click |

## Checklist (every message)

- [ ] It is named as an indicator, a validation or a notification, and uses that kind's component
- [ ] Indicators sit on their subject, show only while true, and never rely on colour alone
- [ ] Validations sit under their field, in the form's words, stay until fixed, and are announced
- [ ] Action-required: a warning panel with its button, or a dialog only when the app must ask
- [ ] Passive: in place, persistent, never a toast
- [ ] A 403 is a permission notice, never an error
- [ ] Nothing important disappears on a timer
