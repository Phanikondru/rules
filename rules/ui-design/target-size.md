# Target size — big enough, close enough, far enough apart

Applies to **every clickable or tappable thing**: buttons, icon buttons, row
subjects, row actions, chip remove controls, pager buttons, navigation items,
menu items, checkbox rows, map markers. It also applies to **where a control
sits** relative to the thing the person used just before it. Sources:
[Fitts's Law and Its Applications in UX](https://www.nngroup.com/articles/fitts-law/)
(Raluca Budiu, NN/g, 2022) ·
[Touch Targets on Touchscreens](https://www.nngroup.com/articles/touch-target-size/)
(Aurora Harley, NN/g, 2019).

`button-states.md` decides what a control says about itself. the `ux-laws` skill
names Fitts's Law. This file turns the law into sizes, spacing and placement.
The values stay in the project's design system / style guide doc (e.g.
`DESIGN.md`). This file adds none.

## What the research found

- **Time to hit a target depends on its size and its distance.** Fitts:
  `T = a + b × log₂(2D / W)`. Double the distance and the time grows by a
  step. Halve the width and it grows by the same step.
- **A movement has two phases**: a fast, coarse move toward the target, then a
  slow, careful one to land on it. **The smaller the target, the longer the
  slow phase.**
- **Bigger targets are faster and cause fewer errors.**
- **A label beside an icon makes the target bigger**, as long as the label is
  clickable too.
- **Crowded targets cause overshoot**, especially small ones.
- **Invisible padding prevents misses but does not speed people up.** They
  still slow down for the edge they can see.
- **Screen edges are infinite targets for a mouse**, but **slower on a
  touchscreen**.
- **Controls used one after another belong close together**: the Save button
  near the last field, a menu opening beside its trigger.
- **A linear menu is fastest when the most used item comes first.**
- **On touch, a target is at least 1 cm × 1 cm** (Parhi, Karlson and Bederson,
  2006). A fingertip is 1.6–2 cm wide, and a thumb about 2.5 cm.
- **View–tap asymmetry**: something large enough to see can still be too small
  to tap. Desktop layouts shown on a tablet are the usual cause.
- **Primary actions and hurried contexts deserve bigger targets.**

## Choosing a baseline

Decide, and record in the style guide, what the primary input is.

- **Mouse at a desk**: a compact control height (e.g. 32px, 28px dense) is
  acceptable, with an absolute floor for any target (e.g. 24px, WCAG 2.5.8).
  Do not bump one component to a touch size inside a row of compact controls:
  it breaks the similarity rule the layout depends on.
- **Touch**: NN/g's 1 cm is about 38 CSS px at the reference pixel; platform
  guidelines commonly say 44px. A compact desktop control is under it.
- **Both**: a desktop layout used on a tablet needs a deliberate coarse-pointer
  step (`pointer: coarse`) decided in the style guide, never a per-component
  bump. Until it exists, say which screens are meant for tablet use and name the
  gap.
- **Known gaps to look for**: chip remove controls that are a bare glyph or a
  text `×` with no padding are usually under the floor.

## Rules

### 1. Size

- **Nothing clickable is under the floor** in either dimension. Pad the target,
  not the glyph (`colour-type-icons.md`). A 16px icon sits in a larger button.
- **The visible target is the real target.** The hover background covers the
  whole hit area, so the person can see where it ends. Invisible padding is
  allowed only as extra margin around a target that is already large enough.
- **The label is part of the target.** An icon and its word are one button.
  A checkbox and its label are one `<label>`. A row that opens a record is
  clickable across its subject, not only on an arrow.
- **Row subjects are links across their text**, not on one word of it.
- **The primary action is never the smallest control on the screen.** A
  commit is a full-size button, never a ghost icon.
- **Same kind, same size** (`visual-design.md`). Do not shrink one control in
  a row to make it fit. Move it into the overflow menu instead.

### 2. Spacing

- **Adjacent targets have a gap.** Controls in a row take at least 8px. Icon
  buttons in a tight group (a pager) may take 4px only when each one already
  meets the floor.
- **Opposite actions are never crowded.** Allow beside Refuse is safe only
  because Refuse opens a confirmation. A destructive action that commits at
  once never sits next to a safe one.
- **Dense clusters are split, not shrunk.** Map markers that overlap are
  grouped or offered as a list, not left for a precise click.
- **Fewer targets, each larger**, beats more targets, each smaller. Remove
  before shrinking (`ui-workflow.md`).

### 3. Distance

- **The next control is near the last one used.**
  - A dialog's commit sits bottom right, straight after its fields.
  - A long form page repeats or places its Save at the end of the form, not
    only in the title bar.
  - Row actions sit on the row, not in a toolbar above the table.
  - A dropdown opens from its trigger, never in a distant panel.
- **A control does not move between repeated clicks.** Next page stays in the
  same place as the range text changes width. A button that shifts after a
  load teaches people to look before every click.
- **Menus put the most used item first.** In an overflow menu the destructive
  item comes last, apart from the others.
- **Do not rely on the window edge.** A browser window rarely touches the
  screen edge, so the edge is not an infinite target here. On touch it is
  slower, not faster.

### 4. Touch, where it happens

- **Anything visible is operable.** If a dot, badge or caret can be seen on a
  tablet, it can be pressed, or it is not a control.
- **Nothing depends on hover** (`interactions.md`, rule 1). A tablet has no
  hover.

### 5. Check it

- **Measure the hit area in the browser**, not the glyph: DevTools element
  box, or `getBoundingClientRect()` on the button.
- **Tab through it and click through it** at a desktop and a tablet width.
- **At 200% zoom**, targets grow and still do not overlap.
- **Say whether it was tried on a tablet.** Until it has, say it was not.

## Checklist (every clickable change)

- [ ] Every target meets the floor, measured on the hit area
- [ ] The hover area shows the whole target, and labels are part of it
- [ ] The primary action is a full-size button, and controls of one kind share a size
- [ ] Adjacent targets have a gap, and opposite actions are not crowded
- [ ] The next control is near the last one used, and nothing shifts between clicks
- [ ] Menus lead with the most used item, with the destructive one last
- [ ] No touch-size bump in one component, and any tablet use names the coarse-pointer gap
- [ ] Checked in the browser, and "untested on a tablet" stated where it applies
