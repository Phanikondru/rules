# Self-review — the pass before anyone else looks

Applies to **every UI change, before it is shown, committed or sent for
review**. Source:
[5 Common Mistakes Junior Designers Make](https://www.nngroup.com/videos/junior-designer-mistakes/)
(Kelley Gordon, NN/g, 2024; [video](https://www.youtube.com/watch?v=FIek0K69rbI)).

The five mistakes, and what each one means here:

| # | NN/g mistake | Here |
|---|---|---|
| 5 | Designing for how it looks instead of usability | Rule 1 |
| 4 | Type crimes: dashes, orphans, primes and quotes | Rule 2 |
| 3 | Working outside the design system | Rule 3 |
| 2 | Not presenting the design with confidence | Rule 4 |
| 1 | Asking for feedback too often, with obvious mistakes still in | Rule 5 |

The other rules say how a screen should be. This one is the habit that catches
what they missed, before a reviewer has to.

## Rule 1: usable first, then good-looking

NN/g: aim for designs that are "visually compelling and highly usable", and
test them with real users.

- **Name the task the screen serves** before judging how it looks
  (`ui-workflow.md`, One decision per screen).
- **Walk the task in the browser**, against a live API, from the keyboard as
  well as the mouse. A screenshot is not a test.
- **Walk the states a screenshot hides**: loading, empty, error, permission
  denied, a long name, a zero, a hundred rows.
- **A visual idea that costs the task loses** (the `ux-laws` skill,
  Aesthetic-Usability does not excuse a flaw).
- **Say whether real users have used it.** Until they have, say it is untested
  with them.

## Rule 2: no type crimes

NN/g names misused em and en dashes, orphans, and misused primes and quotation
marks. Pick conventions like these, write them in the style guide doc, and
apply them everywhere:

- **En dash (–), spaced, for a range**: `2:10 pm – 2:35 pm`, `1 – 30 of 743`,
  `14 Sept – 16 Sept`. Never a hyphen.
- **Em dash (—) for an empty cell**, and nowhere in UI sentences if the voice
  forbids dashes joining clauses (`voice.md`). A code comment may use one.
- **Hyphen (-) only inside a word**: `sign-in`, `mock-location`.
- **Minus (−) for a negative figure**, if one is ever shown.
- **Multiplication sign (×) for a close or remove glyph drawn as text**, never
  the letter x. Prefer the icon.
- **Ellipsis (…) as one character**, and only on a control that opens something
  asking for more, or on in-progress text. Never three full stops.
- **Quotes and apostrophes**: where one is needed in a sentence the reader
  sees, use the typographic ’ and “ ”. Straight ' and " belong in code. If the
  voice avoids contractions, apostrophes are rare.
- **Primes (′ ″) only for measurements**, never as quotes.
- **No orphans** in a heading, empty-state line or dialog description. Use the
  platform's balanced-wrapping for headings and short centred text (for example
  CSS `text-wrap: balance`) and `text-wrap: pretty` for running text. Never fix
  an orphan with a manual `<br>` or a non-breaking space that breaks at another
  width.
- **Numbers**: figures, tabular figures in columns, the audience's locale
  grouping, and times in the locale's format and time zone.
- **Units have a space**: `25 m`, `32 km/h`. **Percent does not**: `98%`.
- **Sentence case**, no double spaces, no trailing spaces, and a full stop on
  every sentence and on no label (`voice.md`).
- **One spelling variant** (for example British or American) and one spelling per
  term. Check the existing copy files first.

## Rule 3: inside the design system

NN/g: "use the colors, icons, font family, and patterns that are already there
for you. In fact, truly talented designers make things feel fresh within these
constraints."

- **Tokens only**: no hex, no arbitrary size, no default grey, no card shadow
  where the system forbids it (`colour-type-icons.md`).
- **Shared components only**, extended rather than forked
  (`ui-workflow.md`, List the components).
- **Icons from the shared icon set**, with the same stroke.
- **A pattern the style guide doc does not cover goes to references first** and
  is written back. A new idea is expressed in the system, not beside it.
- **Freshness comes from composition, hierarchy and restraint**, never from a
  new colour, font or radius.

## Rule 4: present it with the reasoning

NN/g: you are the expert on what you designed, so present it with confidence,
with backup options ready. For work handed back to the user:

- **Lead with the decision and why**, naming the style guide section, the rule
  or the UX law behind it.
- **Name the alternatives considered** and why they lost, in one line each, so
  pushback meets a reason rather than a shrug.
- **State what was not checked**, plainly. Confidence is not overclaiming.
- **Do not reopen a settled decision to please a comment.** Weigh it against
  the style guide doc, and change the doc deliberately if the comment is right.

## Rule 5: review it yourself before asking

NN/g: "Take a pause before you send your work over for feedback." Asking is
fine. Asking with obvious mistakes still in wastes the reviewer's time.

Before showing, committing or opening a PR, pause and check:

- [ ] Spelling and grammar in every new string
- [ ] Rule 2: dashes, quotes, ellipses, orphans, numbers and units
- [ ] Rule 3: tokens, components and icons from the system
- [ ] The four states and the keyboard path, walked in the browser
- [ ] The project's lint, typecheck and build are clean
- [ ] The style guide doc's own linter is clean if it changed
- [ ] No leftover debug logging, commented-out code or stray TODO
- [ ] The style guide doc updated if a pattern was added or changed
- [ ] The summary says what was not checked

Batch the questions. Ask about decisions that genuinely need someone else, not
about things this list would have caught.

## Checklist

- [ ] The task was walked in the browser, states included, before judging the look
- [ ] No type crimes
- [ ] Nothing outside the design system
- [ ] The handover leads with the decision, its reason and the alternatives, and says what was not checked
- [ ] The Rule 5 pass was done before asking for review
