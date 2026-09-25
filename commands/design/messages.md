---
name: messages
description: Check each message on a page is the right kind — indicator, validation or notification — in the right component and place (NN/g, Indicators, Validations, and Notifications)
---

The page, flow or message is `$ARGUMENTS`. Read
`.claude/rules/indicators-validations-notifications.md`,
`.claude/rules/voice.md`, and the style guide doc's sections on chips and
badges, forms, stat tiles and the four states first. Then read the page, the
components it uses, its copy strings and the API error mapping.

1. **List every message**: pills, nav and tab counts, count lines, tiles,
   field errors, form errors, warning panels, error panels, permission notices
   and dialogs. Include the loading, error and permission-denied states.
2. **Name each one's kind**: indicator, validation, or notification
   (action-required or passive). Use the rule file's "Picking the kind".
3. **Check the component** against the rule file's table. A mismatch is a
   finding.
4. **Indicators**: on their subject, shown only while true, refreshed by the
   event, never colour alone.
5. **Validations**: under the field, in the form's words, stay until fixed,
   announced, and input kept.
6. **Notifications**: action-required ones interrupt only as much as needed,
   and passive ones persist in place. Nothing is on a timer, there is no toast
   (unless the project allows them), and there is no `window.alert`.
7. **Refusals**: a disabled control with no visible reason is a finding.

Report findings as: the message, its kind, what happens, which rule it breaks
(with its NN/g source), and the fix. Hand wording to `/copy`. Do not change
code unless asked. When fixing, run the project's lint, typecheck and build.
