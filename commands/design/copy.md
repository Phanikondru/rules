---
name: copy
description: Write or review the words on a page — buttons, dialogs, errors, empty states, pills, permission text — against the project's voice rules
---

Write or review the copy for `$ARGUMENTS`. The rules are in
`.claude/rules/voice.md`, so read them first.

1. **Find the existing words.** Read the relevant copy files, the API error
   mapping, and sibling pages. Reuse a term that already exists, and do not
   introduce a synonym.
2. **Write for the reader** defined in the project's voice rules (who they are,
   what language fluency to assume, what they are doing). Short, plain, in the
   project's register.
3. **For each string, check:**
   - a button names its outcome
   - a dialog title is the question, and its description states the consequence first
   - an error says what happened, then what to do, with no field names or codes
   - an empty state has a headline and one sentence, and its glyph matches its meaning
   - status is the plain register, never the enum
   - permissions are plain English, never a key
   - a decline is neutral
4. **Check the type**: dashes, quotes, ellipses and orphans, per
   `.claude/rules/self-review.md`, Rule 2.
5. **Check the fit**: in the narrowest column, a table cell and a dialog, the
   string fits as designed (one line where the style guide doc says so).
6. **Check honesty**: read each sentence against what the code actually does
   (the confirm handler, the API call). The words never promise more than the
   button delivers.

Report the strings as a before and after list, with a one-line reason for each
change.
