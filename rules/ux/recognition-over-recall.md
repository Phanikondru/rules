# Recognition over recall — the screen holds what the person would otherwise remember

Applies to **every screen where a person must know something to act**: field
entry, filters, search, commands, icons, records that refer to other records,
and a queue worked across several pages. Sources (NN/g):
[Memory Recognition and Recall in User Interfaces](https://www.nngroup.com/articles/recognition-and-recall/)
(Raluca Budiu, 2024) ·
[10 Usability Heuristics](https://www.nngroup.com/articles/ten-usability-heuristics/)
(Jakob Nielsen, heuristic 6, "Recognition rather than recall").

**A warning about a source.** The URL
`nngroup.com/articles/recall-beats-recognition/` is Nielsen's April Fools' 2022
joke, "Support Recall Instead of Recognition in UI Design". It argues for
numeric command codes, meaningless icons and "You know what to do here"
tooltips, and says so at the end. **It is not a guideline.** It is the reverse
of this file, and it is a fair list of what not to build. Do not cite it as
support for recall.

the `ux-laws` skill names Cognitive Load and Working Memory. `interactions.md` rule 1
says nothing is memorised. This file turns them into checks for what the screen
must show.

## What the research found

- **Recognition** is knowing a thing when you see it. **Recall** is retrieving
  it from memory with few cues. Recognition needs more cues, so it is easier.
- Menus, results pages and recently viewed lists are recognition. Passwords,
  command lines and hidden gestures are recall.
- **Make information visible and reachable** so nobody has to memorise it.
- **Keep history and recent items**, so a person can retrace and resume.
- **Let people save things** and pick them back later.
- **Replace command languages with visible controls.**
- **Give tips where they apply**, not a general tutorial.
- **Label icons.** An icon alone is recall.

## Applying it

Trained users who work the same queue daily have some real recall expertise,
and that is fine. The rule is not to remove it. The rule is that **nothing
required to finish a task lives only in the person's head, or on another
screen**.

| Guideline | In the product |
|---|---|
| Visible, not memorised | Navigation lists every page. No shortcut is the only way (`interactions.md`) |
| Labelled icons | A word beside the glyph (`colour-type-icons.md`) |
| Contextual help | Help tips and hints under fields. No tour (`web-ux.md` §1) |
| Filters visible | Filter chips (the project's style guide) |
| Value acted on shown | "Allow 3 days for <name>?" (`reading.md` §6) |
| History and recents | Only if the project has decided to build them. Otherwise the URL and Back |
| Saved items | Same |

## Rules

### 1. Pick from what exists, do not type what is remembered

- **A field whose answer is a known set is a dropdown or multi-select**, never a
  text box the person must fill from memory. Places, roles and people are picked
  by name.
- **Add search once a list passes about eight options**, so a long list is
  recognised by typing the first letters.
- **Show the name, not the id.** A record refers to a person or a place by the
  words users use. A generated id is never the only label
  (`dense-pages.md`, rule 7).
- **Never ask for a value the system already holds.** Fill it in and say so
  (`web-ux.md` §5).

### 2. Keep the context on screen

- **The value being acted on sits beside the action**, so nobody must carry it
  across a scroll or a page (`reading.md` §6).
- **A dialog names its subject** in the title or description ("Close <place>?").
- **A side sheet keeps the list behind it**, so the row is still visible and
  marked.
- **Do not split one decision across screens.** The figure needed to decide is
  on the deciding screen, for example a person's leave history in the leave
  queue.
- **A long form shows what was already answered**, and never asks the person to
  remember an earlier step.

### 3. State is visible

- **Every applied filter is a removable chip** (`forms-and-selection.md`). A
  filter left on and forgotten is a recall failure.
- **The scope trail** says which subset of data is shown.
- **The chosen row stays marked** after a sheet opens.
- **Back returns to the same row, with filters, sort and page kept**
  (`web-ux.md` §4).
- **A record's status and history are on the record**, not remembered from
  yesterday (`async-and-status.md` rule 10).

### 4. Words beside glyphs, and no codes

- **A visible label by default.** Icon-only is allowed only where
  `colour-type-icons.md` lists it, with an `aria-label`. A tooltip is not the
  label.
- **No numeric or letter codes as the way to act.** Nothing is typed as a
  command. Enum values and permission keys are shown in plain words
  (`voice.md`).
- **The one exception is a code the organisation already uses and prints**, such
  as a complaint or reference number. It sits beside the name, and search
  accepts either.
- **No generic tooltip.** A help tip says the specific thing about that
  control, and holds nothing required (`control-size.md` rule 8).

### 5. Recall is allowed only where it protects

- **Passwords and OTPs are recall on purpose.** Support them: reveal control,
  the browser's credential manager, and the correct `autocomplete`
  (`web-ux.md` §5).
- **Do not ask for a memorised secret to authorise a routine action.**
- **A person must never need to remember a rule to avoid an error.** Show the
  rule the API states, beside the field, before submit
  (`motion.md`, live requirement feedback).

### 6. Recents and saved items are a decision, not a default

- **Search history, recently opened records and saved views are added
  deliberately.** A request for one goes through `feature-value.md` and a
  reference-product check, and is written into the project's style guide.
- **The URL is the free version.** State worth returning to (drill-down, record,
  day, filters) is in the URL, so a bookmark or Back recognises it
  (`web-ux.md` §0).

## Checklist (every screen that asks the person to know something)

- [ ] A known set is picked, not typed, and searchable past eight options
- [ ] Records are named in users' words, never only by an id
- [ ] The value acted on is beside the action, and a dialog names its subject
- [ ] Applied filters and scope are visible
- [ ] Back and closing a sheet keep the person's place
- [ ] Every icon has its word, and nothing is done by typing a code
- [ ] Any hint is specific, and nothing required lives only in a tooltip
- [ ] Recents or saved items were not added without a recorded decision
- [ ] The April Fools' article was not cited as a source
