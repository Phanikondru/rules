---
name: ux-audit
description: Audit a page or flow against every design rule at once — style guide, UX laws, visual design, colour, type, motion, interactions, reading, scroll, web UX, buttons, target size, specs, forms, states, messages, voice, self-review — and report findings with their source
---

Audit `$ARGUMENTS`. This is a review, not a rebuild. Do not change code
unless asked.

## 1. Read

- The project's style guide doc (e.g. `DESIGN.md`): tokens and layout, and the
  component sections the screen uses.
- The page, its route, the components and hooks it uses, and its copy strings.
- Every rule in `.claude/rules/`:
  - `ui-workflow.md`
  - `feature-value.md`
  - `colour-type-icons.md`
  - `colour-use.md`
  - `typefaces.md`
  - `async-and-status.md`
  - `indicators-validations-notifications.md`
  - `forms-and-selection.md`
  - `voice.md`
  - the `ux-laws` skill
  - `motion.md`
  - `interactions.md`
  - `reading.md`
  - `recognition-over-recall.md`
  - `dense-pages.md`
  - `scroll-fading.md`
  - `web-ux.md`
  - `button-states.md`
  - `target-size.md`
  - `control-size.md`
  - `design-specs.md`
  - `self-review.md`
  - `visual-design.md`
  - `style-guide.md`

## 2. Name the screen's one decision

What the person opened it to do, what leads, and what is supporting.

## 3. Walk the rules

Go through each rule file's checklist against the screen. Where a finding is a
judgement call, name the UX law that settles it (the `ux-laws` skill). Cover the
states a screenshot does not show: loading, empty, error, permission denied,
busy, the smallest supported widths, 200% zoom, keyboard only, reduced motion,
and the screen reader. If the app can be run (`/run`, or the Chrome tools), look
at it. Otherwise say the audit was from the code.

## 4. Report

Group findings by severity:

1. **Misleads or loses work**: honesty, lost input, a hidden filter, a
   client-side count, a 403 shown as empty.
2. **Blocks or confuses the task**: hierarchy, keyboard traps, navigation,
   unreadable text.
3. **Inconsistent with the system**: tokens, components, copy terms.
4. **Polish**, including type crimes.

For each finding, give:

- `file:line`
- what the person experiences
- the rule broken, and its source (the style guide section, the rule file, or
  the law or NN/g article)
- the fix

End with what the style guide doc does not cover (these need references first),
any place the doc and the token config disagree, and what could not be checked
without a browser or a live API. Do not invent findings. A clean area is
reported as clean.
