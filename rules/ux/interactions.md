# Interactions — pointer, keyboard and overlays: nothing to memorise, nothing by accident

Applies to **every interaction beyond a plain click**: hover, keyboard, menus,
flyouts, dialogs, sheets, media viewers, map interaction, confirmations, and
where alerts and hints appear. Sources:
[Keyboard-Only Navigation](https://www.nngroup.com/articles/keyboard-accessibility/) ·
[Tooltip Guidelines](https://www.nngroup.com/articles/tooltip-guidelines/) ·
[Modal & Nonmodal Dialogs](https://www.nngroup.com/articles/modal-nonmodal-dialog/) ·
[Confirmation Dialogs](https://www.nngroup.com/articles/confirmation-dialog/) ·
[Accidental Overlay Dismissal](https://www.nngroup.com/articles/accidental-overlay-dismissal/) ·
[Cancel vs Close](https://www.nngroup.com/articles/cancel-vs-close/) ·
[Kinect Gestural UI: First Impressions](https://www.nngroup.com/articles/kinect-gestural-ui-first-impressions/)
(its general lessons: visible not memorised, feedback that says why, alerts
where the eye is, one meaning per action, consistent protection against
accidents) ·
[Overuse of Overlays](https://www.nngroup.com/articles/overuse-of-overlays/) ·
[Popups: 10 Problematic Trends](https://www.nngroup.com/articles/popups/) (all NN/g).

## Establish the interaction vocabulary

Before changing interactions, list what the product uses today (click, hover,
keyboard, overlay types, URL state) and keep to it unless the project's style
guide changes first. A typical desktop product uses:

- **Click**: everything.
- **Hover**: colour feedback, flyouts, and detail on maps or charts.
- **Keyboard**: Tab order, Escape on overlays, arrow keys in tabs, dropdowns
  and flyouts.
- **Overlays**: a centred modal dialog and a side sheet showing a record. A
  dialog may open over a sheet.
- **URL state**: drill-downs and selected day or record, so Back undoes the last
  step.

## Rules

### 1. Visible, not memorised

- **Every action is a visible control with a word**, or an icon with an
  `aria-label` where `colour-type-icons.md` allows it.
- **Nothing only on hover.** A flyout also opens on Enter or Space. A row
  action that appears only on hover is also reachable by keyboard focus. Map
  details also exist as list or timeline rows.
- **A tooltip is supplementary** (NN/g). It never carries the only copy of an
  explanation, a reason or a label.
- **No keyboard shortcut is the only way** to do something. A shortcut is shown
  where it applies (e.g. a `⌘K` chip).
- **No tour and no help bubble** unless the project's style guide adopts one.

### 2. A shape must do what it looks like it does

- An **underline** is a link or a link-styled button. A **caret** opens
  something. A **chevron on a row** navigates. A **grip** can be dragged.
- If the promised interaction is not supported, **support it or remove the
  shape**.
- **Anything that looks clickable is clickable**, and anything clickable shows
  the pointer cursor and a hover state.

### 3. The keyboard reaches everything

- **Tab order follows the reading order.** No positive `tabIndex`.
- **Composite widgets use arrow keys**: tabs, listboxes and menus, with only one
  stop in the Tab order.
- **Escape closes the topmost overlay only.** A dialog over a sheet closes the
  dialog.
- **Focus moves into an overlay, is kept there, and returns to what opened
  it.** A new overlay does the same.
- **Focus follows a swapped region**: when a drill-down replaces a table, focus
  moves to the new table's title.
- **A map is one `role="application"` region.** Its stops are reached from
  list or timeline rows.

### 4. Feedback at once, and it says why

- **Every click responds at once** (`button-states.md`).
- **Every result says what happened**, and a problem points to its cause: the
  error sits under the field.

### 5. Alerts go where the person is looking

- **A problem is shown in the content**, in the section it concerns.
- **An error sits beside the control that caused it**, not beside a distant
  button.
- **Nothing that matters disappears on its own.**

### 6. One interaction, one meaning, everywhere

- **Back undoes the last navigation**, including a drill-down step. It never
  loses typed input silently.
- **Escape and the scrim mean Cancel** on a confirmation. They never commit.
- **Every dialog closes the same way**: Cancel, Escape or the scrim. While
  busy, none of them work.

### 7. Confirm only what is costly, the same way every time

- **Confirm what is costly to undo**: refuse a request, close or remove a
  record, record an exit, sign a device out. Everything else acts at once.
- **Every confirmation uses the same dialog component**: the question as title,
  one line of consequence, Cancel then the outcome button, styled `destructive`
  for a destructive commit. **Never `window.confirm` or `window.alert`.**
- **No confirmation for a safe action.** It teaches people to click through the
  one that matters.
- **Adjacent opposite actions** (Allow beside Refuse) are safe because the
  destructive one opens a dialog.

### 8. Overlays are not closed by accident

- **Prefer a page or a sheet to a dialog** for anything longer than a question
  or a short form.
- **A dialog with typed input does not lose it to a stray scrim click or
  Escape.** Either keep the draft for when it reopens, or ask before
  discarding once something has been typed.
- **Never stack two dialogs.** A dialog over a sheet is the one allowed layer.
- **The close control is visible and labelled.** A sheet's close button says
  `Close <name>`.
- **No overlay the person did not ask for**: no popup on load, no
  "before you go" prompt, and no "come back" tab title
  ([Needy Design Patterns](https://www.nngroup.com/articles/needy-design-patterns/)).
  An overlay opens because of a click.

### 9. Close keeps the work; discarding is its own labelled action

- **Words, not a bare ✕**, on anything holding work: Cancel, Keep editing,
  Discard. An icon-only ✕ is allowed where nothing can be lost (a photo
  viewer, a read-only sheet), with an `aria-label`.
- **Leaving keeps the work by default** where the draft matters.
- **Throwing work away is its own action**, and it states what is lost.

### 10. No hidden or fiddly interactions

- **No drag-only action.** Anything draggable (a reorder or a map pin) has a
  keyboard and typed equivalent (WCAG 2.5.7).
- **No nested menus** and no hover path the pointer must thread (Steering Law).
  A flyout is positioned so the pointer can reach it directly.
- **No slider without a way to type the value.**
- **Targets are at least 24px** (WCAG 2.5.8), and controls use the project's
  target size (`target-size.md`).

### 11. Do the obvious thing, and say so

- **Anything done automatically is visible**: a count that refreshed, an "As
  of" time, and a date left out of the URL meaning today.
- **Never automate a choice that is the person's.**

## Checklist (every interaction change)

- [ ] Every hover or shortcut action has a visible, keyboard-reachable equivalent
- [ ] Every shape that suggests an interaction supports it
- [ ] Tab order follows reading order, and composite widgets use arrow keys
- [ ] Overlays move, trap and return focus, and Escape closes only the topmost
- [ ] Results say what and why, and problems sit beside their cause
- [ ] Only costly actions confirm, always with the shared dialog, never `window.confirm`
- [ ] No stacked dialogs, and a stray click never loses typed input
- [ ] Anything holding work closes with a word, and discarding is labelled
- [ ] No drag-only action, nested menu or bare slider, and targets are at least 24px
