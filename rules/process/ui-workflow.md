# UI workflow — how a screen gets built

Applies to **every UI change**: pages, components, global styles and the theme
or token config. This is a workflow rule, not taste. A change that fails the
checklist at the bottom is not finished.

Companion rules, all of which run on UI work:
- `ideation.md`: how ideas are found before they are judged, and the mindset behind them (NN/g)
- `flow-review.md`: gaps across a flow or area, from scenarios, seams and a map of the domain's nouns (NN/g)
- `feature-value.md`: whether the thing should exist, and the cheapest form that shows it (NN/g)
- `colour-type-icons.md`: whether it can be read at all
- `async-and-status.md`: whether the product ever goes quiet
- `indicators-validations-notifications.md`: which kind of message, in which component (NN/g)
- `forms-and-selection.md`: fields, spacing, the chosen state
- `voice.md`: what the screen says
- the `ux-laws` skill: the named law that justifies a decision (lawsofux.com)
- `motion.md`: which motion is allowed, and why (motion.zajno.com, NN/g)
- `colour-use.md`: whether a colour should be used at all (NN/g)
- `typefaces.md`: one family, hierarchy by weight, and what a second face would need (NN/g)
- `interactions.md`: pointer, keyboard, overlays, confirmations, where alerts go (NN/g)
- `reading.md`: how much text a screen carries and how it is laid out (NN/g)
- `recognition-over-recall.md`: nothing the person must remember that the screen could show (NN/g)
- `dense-pages.md`: a page with many sections or much data, cut, chunked and summarised (NN/g)
- `scroll-fading.md`: nothing moves on scroll, and more below is obvious (NN/g)
- `web-ux.md`: navigation, permissions, tables, filters, fields, shared desks (NN/g)
- `button-states.md`: enabled, hover, pressed, loading, disabled, focus (NN/g)
- `control-size.md`: control heights, form spacing and width
- `target-size.md`: how big a target is, how far apart, and how far from the last click (NN/g)
- `design-specs.md`: what is written down before a screen is built, and where (NN/g)
- `self-review.md`: the pass before anyone else looks, including type crimes (NN/g)
- `visual-design.md`: hierarchy, Gestalt grouping, similarity, imagery, and how to validate the look (NN/g)
- `style-guide.md`: keeping the project's style guide doc a complete, living front-end style guide (NN/g)

Each has a slash command. `/ux-audit` runs them all.

The values live in the project's style guide doc (e.g. `DESIGN.md`) and its
token config. These rules decide how to apply them. They never restate a hex
code.

## Order of work

0. **Find the ideas first** (`ideation.md`, `/ideate`) when the question is
   "what could this be?", then **know what the screen is for**
   (`feature-value.md`, `/feature`). On a new feature, the goal, the cheapest
   form and where it belongs are settled before a screen is designed. Skip this
   only when the work is a change to something whose goal is already settled.
1. **Read the style guide doc**: values and layout, then components and the
   four states.
2. **Is the pattern already specified?** If yes, build from the spec. Do not go
   to a reference library to reopen a settled component.
3. **If not, look at references**: search a screen-reference library for the
   pattern (name the product's closest reference products first), across three
   or more products. Take the structure, never the skin.
4. **Write the spec** for a new screen or feature (`design-specs.md`,
   `/spec`) before the code.
5. **One reference decides the look**, and another may decide how a
   domain-specific screen is composed. Name them in the style guide doc. No
   other reference changes a token.
6. **Build from the project's tokens**, never raw values.
7. **Write the new pattern back into the style guide doc** in the same commit,
   with the reference links. A value shared with another codebase (accent, ramp,
   status, typeface) also changes there.

Where the style guide doc and the token config disagree, **say so**. Do not
silently pick one. The config is what ships; the doc is what gets corrected.

## List the components before writing one

Before writing a new component, list the project's shared components (shell,
navigation, tabs, table and its loading/empty states, pager, sort header,
filters, button, text field, textarea, select, dropdown, multi-select, field
layout, dialog, side sheet, status pill, stat tile, form error, permission
notice, full-page spinner, icons) and state which already covers it and what is
genuinely missing. Check the feature folders for domain tables, dialogs and copy
files before building a sibling.

**Extend a shared component before adding a variant.** A one-off that looks
right on one screen is still a net loss, because the next screen will not
match it.

## One decision per screen

Name what the person opened the screen to do. That is the loudest thing on it.
Everything else is supporting and steps down.

- **One accent element per screen**, not counting the navigation's current
  page. Two filled primaries is the defect.
- **At most one status pill per row.**
- **Remove before adding.** When asked to "improve" a screen, the first move is
  subtraction.
- **Negative space is emphasis.** Do not fill it.

## Colour budget: 60 / 30 / 10

Define it in the style guide doc, measured by area:

- **60%**: the work. Cards on the canvas, lines, ink.
- **30%**: the navigation panel or secondary surface.
- **10%**: the accent. The current page, the primary button, actionable counts.

Fix a failing screen by **demoting**: make a second primary secondary, drop a
decorative status icon, un-tint a header. Never by adding a competing colour.
**Measure it from a screenshot**; do not guess from the class names.

**One colour, one meaning, everywhere.** The accent means "you can act on
this". It is never a status, a decoration or a chart series beside a button.

## Where the committing action sits

- **Page-level action** (Add item, Raise request): the shell's actions slot, top
  right, beside the title.
- **In a dialog**: bottom right, Cancel then the commit. The commit names the
  outcome.
- **Row actions**: on the row (Allow and Refuse), or in the row's overflow menu
  when there are more than two. The destructive one opens a dialog.
- **A form in a dialog** keeps the footer pinned once the body can outgrow the
  viewport. The field errors stay beside their fields, not beside the button.
- **Enter submits** a single-form dialog or page.

## Design for the real user

Describe the real user and setting in the style guide doc (who, at what device,
doing what). Then:

- **Check at the smallest supported laptop width** and at the next breakpoint
  down (with any side navigation narrowed). Nothing the screen exists for is cut
  off. Wide tables scroll inside their card.
- **Controls have one standard height** (e.g. 32px on a dense desktop tool, use
  your project's token). Icon buttons have at least a 24px target (WCAG 2.5.8).
- **Everything works from the keyboard**, with a visible focus ring.
- **Browser zoom at 200% loses nothing** (WCAG 1.4.4).
- **Reduced motion is honoured** globally.

## Honest screens

A person misled by the product approves the wrong request or concludes that
nothing is wrong.

- **A dialog's sentence promises only what its button does.** Read the copy
  against the handler, not against the ticket.
- **A filter left on is visible** as a chip or a count line.
- **A headcount is the server's count**, never a tally of the rows below it.
- **An unreadable section and an empty one are different facts.**
- **If someone would feel tricked on finding out how a screen works, the
  screen is wrong**, whether or not anyone meant it.

## Push back on vague requests

"Make this screen look better" becomes: **what one decision, what leads, which
shared component is missing, which style-guide rule it breaks.** State that
before building.

## Checklist (every UI change)

- [ ] Style guide doc read. The pattern is either already specified, or referenced
      across three or more products and written back with links
- [ ] Contested choices name the UX law that settles them (the `ux-laws` skill).
      Each rule file's own checklist is run where it applies
- [ ] Shared components used or extended, with no one-off variant
- [ ] Tokens only: no raw hex, no arbitrary size, no default grey, no
      shadow on a card (where the system forbids it)
- [ ] One accent element, one hero, at most one pill per row
- [ ] Passes 60/30/10, and no colour is reused with a second meaning
- [ ] Empty, loading, error and permission-denied states built in the same
      change
- [ ] Committing action placed per the rule above
- [ ] Works at the smallest supported widths, from the keyboard, at 200% zoom
- [ ] Dialog copy matches what its button does, and no filter is hidden
- [ ] The page passes `visual-design.md`, and the style guide doc is updated per `style-guide.md`
- [ ] `self-review.md` pass done before showing it to anyone
- [ ] The project's lint, typecheck and build are clean
- [ ] The style guide doc's own linter is clean if it changed
