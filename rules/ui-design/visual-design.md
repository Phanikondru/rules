# Visual design — hierarchy, grouping and restraint, and how to check them

Applies to **any decision about how a page looks as a whole**: layout,
alignment, hierarchy, density, grouping, imagery and icon weight. It sits above
`colour-use.md` and `colour-type-icons.md`, which settle single values. Sources
(NN/g):
[Visual Design: Glossary](https://www.nngroup.com/articles/visual-design-cheat-sheet/) ·
[Good Visual Design, Explained](https://www.nngroup.com/articles/good-visual-design/) ·
[The Anatomy of a Good Design](https://www.nngroup.com/articles/why-does-a-design-look-good-part2/) ·
[Similarity Principle](https://www.nngroup.com/articles/gestalt-similarity/) ·
[Using Imagery in Visual Design](https://www.nngroup.com/articles/imagery-in-visual-design/) ·
[Flat UI Elements Attract Less Attention](https://www.nngroup.com/articles/flat-ui-less-attention-cause-uncertainty/) ·
[Validate Your Visual Design: 6 Methods](https://www.nngroup.com/videos/validate-visual-design/).

Values stay in the project's design system / style guide doc (e.g. `DESIGN.md`)
and its theme config. This file names none.

## NN/g's advice, and where a design system answers it

| NN/g | Answer in the design system |
|---|---|
| Use a grid, and align to it | A page frame, breakpoints and a spacing base unit |
| About three type sizes on a screen | Body does most of the work, one title leads, one caption size supports. A screen using more than four sizes is a finding |
| Two to four colours, monochromatic is easiest | One brand hue on a matched neutral ramp, plus status (`colour-use.md`) |
| Avoid neon and distracting colour | Status fills used only for shapes and pills |
| Icons match text weight | One stroked icon set beside the text weights (`colour-type-icons.md`) |
| Subtle shadows for depth | A choice to record: flat cards with a border, or shadows. Either way, separation comes from a consistent background/surface step |
| Background shifts at the same saturation | Canvas, sunken and soft-accent backgrounds are all low-saturation steps |

## Rules

### 1. Hierarchy: one thing leads

- **Visual hierarchy** is built by scale, then contrast, then grouping. The
  title leads, the one accent element is the action, and figures that matter
  are set heavier.
- **Something important is clearly larger**, about 30–50% (NN/g), not one pixel
  larger. A 14px to 20px step is such a step. 14px to 13px is not, so it never
  marks importance.
- **Visual weight is a budget.** Dark fills, size and contrast all spend it. A
  decorative block never outweighs the work.
- **Signal-to-noise** ([NN/g](https://www.nngroup.com/articles/signal-noise-ratio/)):
  every element either carries information or groups it. Delete the rest:
  redundant labels, repeated values, borders inside borders. Emphasis is used
  sparingly, because emphasising everything emphasises nothing.
- **Noise depends on the task.** Navigation is noise while reading a list and
  signal while moving between pages. It stays in the same place on every page so
  people learn to ignore it until they need it. A control that moves between
  pages is "malign noise".

### 2. Grouping: the Gestalt principles, in cost order

Proximity first, then continuity, then similarity, and a boundary last.

- **Proximity**: the space inside a group is smaller than the space around it.
- **Common region**: a card groups, but only when proximity is not enough.
- **Connectedness**: a guide line or timeline rail ties items together.
- **Figure/ground**: overlays sit on a scrim, and cards on the canvas.
- **Closure**: a cut-off column says "there is more" (`scroll-fading.md`).
- **Common fate**: things that move together belong together. Only one thing
  moves at a time (`motion.md`).

### 3. Similarity means the same kind, and nothing else

NN/g: items that share a visual trait are read as related.

- **Everything clickable of one kind looks the same on every page.** Row
  subjects, buttons and tabs each have one treatment.
- **Nothing that is not clickable borrows those traits.** No underline on plain
  text, and no accent on a label.
- **Reserve the distinct treatment for the primary action** (NN/g: colour sets
  primary apart from secondary).
- **Same kind, same size**: every control in a row is one height, every pill in
  a column is the same size, and every tile in a row is the same height.
- **Do not reuse a glyph for an unrelated thing** (NN/g: near-identical icons
  suggest a link that is not there).
- **Use dissimilarity on purpose**: a red figure only when non-zero, and the one
  filled button.

### 4. Flat, but never ambiguous

NN/g found flat elements draw less attention and cause uncertainty about what
can be clicked.

- **Every clickable element carries a signifier that is not only colour**: a
  border (buttons and inputs), an underline (links), a caret (dropdowns), a
  chevron (rows that navigate), or a pointer cursor with a hover state.
- **Ghost buttons sit beside something that explains them** (a row, a
  toolbar), never floating alone.
- **Text that looks like a heading is never clickable, and the reverse.**

### 5. Density and whitespace

- **Density is correct for a register.** Whitespace is still a tool: it
  separates groups and gives the one thing that matters room.
- **Clutter test**: if a row carries a title, subtitle, pill, menu and link, it
  carries about two things too many.
- **Balance**: asymmetric by default. The work sits left, the actions sit right,
  and numbers end on the card's right edge.

**Whitespace is balanced, not maximised** ([Whitespace](https://www.nngroup.com/videos/whitespace/),
NN/g). Too tight and ascenders run into descenders. Too loose and the eye cannot
tie a label to its value. Two tools get it right: **a consistent spacing
system** (a base unit and named steps, never an off-scale value), and
**proximity** (less space between related things, more between unrelated ones).

### 6. Imagery and graphics

- **Images carry information or are left out.** Evidence photos and maps earn
  their place. No decorative stock photos and no illustration on a working page.
  Where the design system allows a decorative illustration (an empty state, a
  sign-in panel), it is a recorded exception with a reserved slot, native
  readable copy beside it, and empty alt text.
- **Photos are shown the same way everywhere**: the same tile size, radius and
  provenance marker.
- **Icon stroke matches text weight**: one set, one stroke width.
- **High data-ink ratio in charts**: no 3D, no shadows, and gridlines only where
  they help reading. Series colours follow the categorical order.
- **Alt text says what the image shows** when it carries information ("Photo of
  the gate, taken 2:43 pm"), and is empty for decoration. It never repeats a
  visible caption.
- **Vector for marks and icons, raster for photos.** Photos are served at the
  size shown.

### 7. Brand placement

- **The mark sits at the top left** of the navigation and of the sign-in page.
  NN/g measured 89% better brand recall at top left than at right. Do not centre
  it or move it right.
- **Use one shared logo component**; the collapsed navigation shows the symbol
  alone.
- **The mark is the product's name, not decoration**: give it an `aria-label`
  with the product name.

### 8. Proportion: the system's steps, not a formula

[The Golden Ratio and UI Design](https://www.nngroup.com/articles/golden-ratio-ui-design/)
(NN/g) presents φ (1.618) as one way to derive sizes, and notes that many
designers hold it "no more valid than any other method". Do not derive sizes
from it when the project already has a type ramp, spacing scale and
breakpoints. A proportion argument never introduces an off-ramp size. NN/g's
one lasting point does apply: line height grows as the measure grows, so running
text takes a looser line height than a one-line label at the same size.

### 9. Type, in the glossary's terms

[Typography Terms: Glossary](https://www.nngroup.com/articles/typography-terms-ux/)
(NN/g). Use these words in reviews and specs.

- **Typeface**: one family (`typefaces.md`). **Weights** all loaded, so the
  browser never fakes one.
- **Alignment**: left-aligned text everywhere (NN/g prefers it for
  scanning). Centre only for an empty state or a short single line. Numbers in
  columns are right-aligned. Never justify text.
- **Leading**: the token's line height, and never a tighter override.
- **Tracking**: only an uppercase overline style carries letter-spacing. No
  tracking on body text.
- **Decoration**: underline means a link. No strikethrough except a withdrawn
  value that must stay visible. No text shadow, and no italics for emphasis
  (use weight).
- **Orphans**: avoided in headings and short blocks.
- **Dashes**: en dash for ranges, em dash for an empty cell.
- **Monospace**: avoid. Figures use `tabular-nums` instead.
- **Small caps**: avoid. Column headers use the uppercase overline style.

### 10. Validate it; you are not the user

From *Validate Your Visual Design*. Pick the cheapest method that answers the
question, and say which was used.

| Question | Method |
|---|---|
| Does the hierarchy read? | **Squint test**: blur the screenshot. The title, the primary action and the figures that matter should still stand out |
| Is the first impression right? | **5-second test** with a real user, without warning them it is timed |
| Do people know where to click? | **First-click test**: give a real task and stop after the first click |
| Which of two versions? | **Preference test**: two or three versions that differ in one visible way |
| During a usability session | Ask about the look **after** the task, never before |
| Where does the eye go? | Eyetracking or A/B testing, which are rarely available |

Until one of these has been run with the real audience, say that the design is
untested with them.

## Checklist (every screen-level visual decision)

- [ ] One thing leads, and important things are clearly larger (about 30–50%)
- [ ] Grouping by proximity first, with a boundary only when needed
- [ ] Clickable things of one kind look identical, and nothing else borrows their look
- [ ] Every clickable element has a non-colour signifier
- [ ] No more than four type sizes, with colour and shadow per the style guide
- [ ] Images carry information, have alt text, and match each other
- [ ] Mark at top left
- [ ] The squint test passes on a screenshot, and any user validation is named, or its absence stated
