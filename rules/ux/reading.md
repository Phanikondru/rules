# Reading — people scan, so structure carries the meaning

Applies to **any page, sheet or dialog with more than one sentence**: dialog
descriptions, empty states, record details, long bodies of text, help lines and
error panels. Sources:
[How Users Read on the Web](https://www.nngroup.com/articles/how-users-read-on-the-web/) ·
[F-Shaped Pattern of Reading](https://www.nngroup.com/articles/f-shaped-pattern-reading-web-content/) ·
[Inverted Pyramid](https://www.nngroup.com/articles/inverted-pyramid/) ·
[Layer-Cake Pattern](https://www.nngroup.com/articles/layer-cake-pattern-scanning/) ·
[Scanning Is Optimized for the Task](https://www.nngroup.com/articles/eyetracking-tasks-efficient-scanning/) ·
[First 2 Words](https://www.nngroup.com/articles/first-2-words-a-signal-for-scanning/) ·
[Legibility, Readability, and Comprehension](https://www.nngroup.com/articles/legibility-readability-comprehension/) ·
[Satisficing](https://www.nngroup.com/articles/satisficing/) ·
[Mobile Content Is Twice as Difficult](https://www.nngroup.com/articles/mobile-content-is-twice-as-difficult-2011/)
(for the narrow breakpoints) (all NN/g).

`voice.md` decides the words. This file decides **how much text a screen
carries and how it is laid out**.

## What the research found

- **People scan rather than read.** Most read word by word only when they must.
- **Scanning follows an F shape** on unstructured text. The start of lines and
  the top of the page get the attention, and the rest is skipped.
- **Structure breaks the F.** With clear headings the eye follows a **layer
  cake**: it jumps from heading to heading and reads the body only where it
  matters. That is efficient, and it is what a page should allow.
- **Scanning follows the task.** Someone comparing figures runs down one
  column; someone hunting a name reads only the subject column. A layout that
  keeps each kind of value in the same place on every row serves both.
- **People read about 28% of the words** on a page, and settle for the first
  thing that looks good enough (satisficing).
- **Difficult text is understood much less well on a small viewport.** At
  narrow breakpoints, keep it shorter still.

If the audience reads in a second language, reads the same screens all day, or
works under time pressure, expect the effect to be larger than in the studies.

## Rules

### 1. Lead with the point

- **The first words of a line carry it**: the state, the consequence, or what
  to do.
- **A dialog's description is one or two sentences**, and the consequence
  comes first.
- **An empty state is one headline and one sentence.**

### 1b. Legible, readable, comprehensible (Nielsen)

- **Legible**: the type tokens, AA contrast, and the browser's own zoom
  respected.
- **Readable**: short words, short sentences, active voice. NN/g targets an
  8th-grade level for consumers and 12th for educated B2B readers. If readers
  use English as a second language, **aim at the consumer level or below**, even
  for a B2B tool (e.g. 6th grade on landing and sign-in pages, 8th grade
  elsewhere), per
  [Lower-Literacy Users](https://www.nngroup.com/articles/writing-for-lower-literacy-users/).
- **Comprehensible**: the person's own terms, the point first, and a table or
  diagram where it helps.

### 1c. Some readers plough rather than scan

NN/g found that lower-literacy readers read word by word, have a narrow field of
view, miss anything outside the main column, and lose their place when they
scroll. So:

- **The main point is at the top, in the main column**, never only in a side
  panel or a flyout.
- **Nothing important depends on animation or a fly-out menu.** A flyout
  mirrors pages the expanded navigation shows as static text.
- **One main column of reading** per region. A side panel holds a list or a
  record, not a second article.
- **Search tolerates misspelling** where the API supports it, and a no-results
  state suggests the likely match.

### 2. Structure, not paragraphs

- **Values stand out as values**: a count, a time or a name is in a heavier
  weight or its own cell, never buried in a sentence.
- **Tables over sentences** for anything with more than two attributes
  (NN/g: a register is read down a column).
- **Lists over commas**: three things are three lines.
- **Sections have a title**, with more space around the group than inside it.
  **A heading is descriptive, succinct, and leads with its key word**, and it
  covers everything in its section and nothing else. It never looks like a
  promotion.
- **The first two words of a heading, row label, button or list item carry
  it.** "Absent today", not "Staff who are absent today". "Leave waiting", not
  "Requests for leave that are waiting".
- **A record's related lists are tabs**, not a long scroll.

### 3. Keep the measure

- **Prose is 40–60 characters per line** at every breakpoint: empty-state
  hints, long bodies and dialog text. A full-width paragraph across a desktop
  monitor is not read.
- **Table cells are exempt**, but a cell that wraps to three lines should be a
  detail in a sheet instead.

### 4. Defer the detail

- **Secondary information goes behind a click**: a sheet, a history dialog, or
  a tab. It does not go into a longer paragraph.
- **Remove before shortening.** If a sentence does not change what the person
  does, cut it.
- **A column that repeats one value is removed.**

### 5. Nothing important depends on long text being read

- **A consequence is in the dialog's description or on the button**, not in a
  paragraph above the form.
- **A warning that matters is a panel**, short, with its action, and not a
  sentence in the middle of a card.

### 6. Keep context on screen

- **Show the value being acted on** next to the action ("Allow 3 days for
  <name>?").
- **Do not split one decision across a scroll.** The question and its answers
  are in one view.
- **Say where the figures are from** (the scope trail).

## Checklist (every text-heavy screen)

- [ ] The first two words of each heading, label and line carry the point
- [ ] Headings let the eye layer-cake the page
- [ ] Values stand out, and tables or lists replace comma sentences
- [ ] Prose held to a 40–60 character measure
- [ ] Detail deferred to a sheet, dialog or tab
- [ ] Nothing important depends on a paragraph being read
- [ ] The value acted on is shown beside the action
- [ ] Checked at a narrow width and at 200% zoom
