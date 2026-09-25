---
name: controls
description: Check a form's control heights, spacing and width against the project's recorded geometry — one control height, label gaps, commit spacing, the narrow one-task form, and help tips
---

The form, dialog or page is `$ARGUMENTS`. Read
`.claude/rules/control-size.md`, the project's design system / style guide doc
(e.g. `DESIGN.md`) sections on forms and buttons, and the shared field, button
and help-tip components first.

Open the page in the browser at a fixed desktop width and measure with
`getBoundingClientRect()`:

1. **Heights**: every field, trigger, date field and button is the one
   recorded height. Any other height is a finding.
2. **Gaps**: label to field, field to next label, last field to the commit and
   commit to a following option match the recorded values.
3. **Width**: a one-task form has its fixed width with a full-width commit. A
   dialog form takes the dialog's width.
4. **Sameness**: every control in one form or bar shares its height and body
   type size.
5. **Help**: extra explanation is a help tip beside its control, opening on
   hover and focus and closing on Escape. Nothing required lives only there.

Report each finding with the measured value, the value from the rule, and the
fix. Do not raise a control's height to fix how it looks.
