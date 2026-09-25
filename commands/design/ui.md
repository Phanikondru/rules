---
name: ui
description: Screen or component change intake — works out what a screenshot means, lists the shared components before any code, and applies the style guide so the result fits the design system instead of sitting beside it
---

The request is `$ARGUMENTS`, often with a screenshot. Do the framing work. The
failure this command prevents is a component that copies an image and is wired
in next to the design system rather than into it.

## 1. Work out what the image is

Say which one you assumed:

- **Our screen, reported as wrong**: check it against the style guide doc and
  fix the screen. Where screen and spec disagree, the screen moves, or the spec
  is changed on purpose in the same commit.
- **A design to build**: find which shared components already cover it.
- **Another product's screen**: take the structure only. Every colour, size and
  radius comes from the project's tokens.

## 2. Place it in the flow

One line: what the person just did, and what they do next.

## 3. List the shared components before writing any

From the project's shared component folder (see `.claude/rules/ui-workflow.md`),
state what already covers this and what is genuinely missing. If something is
missing and the style guide doc does not specify it, search a screen-reference
library (three or more products) before building, and write the result back into
the style guide doc with links.

## 4. Name the one decision the screen serves

What leads, and what is supporting. One accent element. At most one pill per
row.

## 5. Build it with the rules

`.claude/rules/ui-workflow.md`, `colour-type-icons.md`, `colour-use.md`,
`async-and-status.md`, `indicators-validations-notifications.md`,
`forms-and-selection.md`, `voice.md`, the `ux-laws` skill, `motion.md`,
`interactions.md`, `reading.md`, `scroll-fading.md`, `web-ux.md`,
`button-states.md`, `visual-design.md`, `style-guide.md`. Name the UX law behind
any choice someone could argue with. Data fetching stays in pages, hooks and the
API layer. Components stay presentational.

## 6. Cover what a screenshot does not show

Skeleton, empty, error and permission-denied states. Busy state on every
control that starts a request. The smallest supported widths, the keyboard path
and focus, 200% zoom, reduced motion, and accessible names.

## 7. Self-review, then report

Run the Rule 5 pass in `.claude/rules/self-review.md`. Then report the
reference links used, what changed in the style guide doc, the checklist from
`ui-workflow.md`, and the lint, typecheck and build results. Say plainly if it
has not been opened in a browser.
