---
name: visual
description: Review how a page looks as a whole — hierarchy, grouping (Gestalt), similarity of clickable things, flat-design signifiers, density, imagery, logo placement — and how to validate it (squint, 5-second, first-click, preference tests; NN/g visual design)
---

The page or design is `$ARGUMENTS`. Read `.claude/rules/visual-design.md`
first, then `colour-use.md`, `colour-type-icons.md` and the project's design
system / style guide doc (e.g. `DESIGN.md`) sections on spacing and components.
Look at the page itself: run it (`/run`, or the Chrome tools) and take a
screenshot at a typical desktop width. If it cannot be run, say so and review
from the code.

1. **Hierarchy**: name what leads. Is it clearly larger or heavier (about
   30–50%)? Count the type sizes on screen. More than four is a finding.
2. **Squint test**: blur the screenshot, or describe what survives at a
   glance. The title, the one accent element and the figures that matter
   should remain.
3. **Grouping**: is proximity doing the work, or have borders been added to
   fix spacing? Check that the space inside each group is smaller than the
   space around it.
4. **Similarity**: list every clickable kind (links, buttons, tabs, row
   subjects, chips). Does each kind look identical everywhere? Does anything
   non-clickable borrow their look? Is a glyph reused for an unrelated thing?
5. **Signifiers**: does every clickable element have a non-colour cue
   (border, underline, caret, chevron, hover)?
6. **Density and noise**: list elements that carry no information and do no
   grouping. Each is a candidate to remove.
7. **Imagery**: do images carry information, match each other, and have
   correct alt text? Are charts free of decoration?
8. **Brand**: is the mark at the top left?
9. **Validation**: say which of the six methods would settle any open
   question, and whether any has been run with real users.

Report findings as: what the person sees, the principle broken (with its NN/g
source), and the fix. Do not change code unless asked.
