---
name: why
description: Settle or justify a design decision with a named UX law (lawsofux.com) instead of taste — "should this be a sheet or a page?", "why are the two actions on the row?"
---

The decision is `$ARGUMENTS`. Read the `ux-laws` skill (`skills/ux-laws/SKILL.md`)
first, and the project's style guide where the decision touches a settled
component.

1. **State the decision as a question**, with its options, in one line.
2. **Read what exists**: the page or component in question, and what the style
   guide already says about it. If the style guide already settles it, say so
   and stop. A law does not quietly reopen a settled spec.
3. **Pick the one or two laws that decide it.** Not a survey. Read each through
   the brief: who the users are, how often they do this, their screens and
   their language.
4. **If laws pull apart**, resolve them with *When laws conflict* in the
   `ux-laws` skill, and say which one won.
5. **Check the NN/g rules that apply**: `interactions.md`, `web-ux.md`,
   `reading.md`, `colour-use.md`, `motion.md`.

Report:

- **Recommendation**, in one sentence.
- **Because**: each law, with one line on how it applies here.
- **Against**: the strongest opposing law, and why it loses.
- **If this changes the style guide**: the line to add to its decisions log,
  citing the law.

Do not change code unless asked.
