---
name: reading
description: Check that a text-heavy page, sheet or dialog can be scanned — point first, structure over paragraphs, measure, deferred detail (NN/g, How Users Read on the Web)
---

The page or text is `$ARGUMENTS`. Read `.claude/rules/reading.md` and
`.claude/rules/voice.md` first. Then read the page and its copy strings.

1. **Point first.** Do the first words of each line carry the state, the
   consequence or what to do?
2. **Scannable.** Are values in a heavier weight or their own cell? Are
   comma-lists turned into lists, and are attributes in a table?
3. **Measure.** Is prose held to 40–60 characters (empty-state hints, dialog
   descriptions, long bodies of text)?
4. **Defer.** List every sentence that does not change what the person does.
   Cut it, or move it into a sheet, tab or history dialog.
5. **Nothing important in a paragraph.** Consequences go in the dialog
   description or on the button. Warnings go in a panel.
6. **Context kept.** The value acted on is shown beside the action, and the
   scope (the trail) is visible.
7. **Narrow and zoomed.** Check at a narrow width and at 200% zoom.

Report a before and after for each string or block, with a one-line reason.
Hand rewording to `/copy` if it needs it.
