# Scroll fading — content is there before the person scrolls to it

Applies to **every scrolling page, table, sheet and list**, and to any proposal
to make something appear, change or animate because of where the person has
scrolled: fade-ins on scroll, collapsing headers, parallax, snapping, lazy
images, counters. Source:
[Scroll Fading 101](https://www.nngroup.com/articles/scroll-fading-101/)
(Sara Paul, NN/g, 2023).

`motion.md` decides which techniques may move at all. This file explains
**why nothing here is triggered by scrolling**, and what a long page does
instead so the person still finds everything on it.

## What the research found

NN/g defines scroll fading as elements that appear or change once the user
scrolls to a certain point, and tested it on live sites:

- **Repeating the animation frustrated people.**
- **It worsens the illusion of completeness.** People took the page as finished
  and never found what faded in below the fold.
- **Fades over 500ms were too slow.** People scrolled past first.
- **Images that faded in on scroll often failed to load.**
- **With scrolljacking** it overwhelmed people.

Someone scanning a register all day is the task-focused user NN/g describes.

## Rules

### 1. Nothing is triggered by scroll position

The project's motion rules should already forbid anything entering on scroll.

- **No fade, slide or scale on scroll.**
- **No scroll-driven motion**: no shrinking header, no parallax, no progress
  bar that fills with scroll.
- **No scrolljacking**: no `scroll-snap` on content, no `scrollTo` or
  `scrollIntoView` the person did not ask for, and no smooth-scroll override.
  Moving focus to a swapped table's title is the one allowed programmatic
  scroll, because the person caused the swap.
- **Pinned is not animated.** A dialog's or sheet's pinned header and footer,
  and a sticky table header, stay still.

### 2. The only appearance is content replacing its skeleton

- **Once per load.** Never again on a refetch or a poll. A periodic refresh
  leaves the rows where they are.
- **Nothing waits on it.**
- **Reduced motion settles the skeleton.**

### 3. Make it obvious there is more

- **The pager sits inside the card and states the range**, e.g. `1 – 30 of 743`.
  A table never looks complete when it is a page.
- **A table that scrolls sideways shows it**: the cut-off column at the card's
  edge says "keep going". Do not size columns so that the last visible one ends
  exactly at the edge.
- **No band of empty space that looks like an end.**
- **A scroll region inside a page shows its scrollbar** and has a visible edge.
- **What the person must see is above the fold** at a typical desktop height:
  the title, the summary tiles, any warning panel, and the first rows.
- **A page that is a workspace does not scroll.** Its regions scroll
  themselves.

### 4. Photos load in place

- **A thumbnail holds its size before it loads**, so nothing below it jumps.
- **A photo appears when it is ready**, not when a scroll position is reached.
- **A photo that fails says so**, with a retry for an expired signed URL. A
  broken-image icon is not a state.

### 5. What NN/g allows it for, and what to use instead

| NN/g use | Instead |
|---|---|
| Progressive disclosure | A sheet, a tab or a history dialog |
| Loading data as needed | The pager |
| Timely supplementary information | A panel in place, shown while it is true |
| Animated counters | Plain figures in tabular numerals. Numbers never count up |

### 6. Screen readers and zoom lose nothing

- **Everything is in the accessibility tree from the start.**
- **200% zoom makes the page longer, not clipped.**

## Checklist (every scrolling page or list)

- [ ] Nothing appears, moves or changes because of scroll position
- [ ] No shrinking header, parallax, snapping or unrequested scroll
- [ ] Refetches and polls leave rows in place with no fade
- [ ] The pager states the range, and sideways scroll is visible
- [ ] What must be seen is above the fold
- [ ] Photos hold their size and say so when they fail
- [ ] Nothing is hidden from a screen reader until scrolled to
