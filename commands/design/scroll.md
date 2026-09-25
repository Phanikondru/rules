---
name: scroll
description: Check a scrolling page, table or sheet — nothing moves on scroll, no unrequested scroll, the pager and sideways scroll are obvious, photos load in place (NN/g, Scroll Fading 101)
---

The page or list is `$ARGUMENTS`. Read `.claude/rules/scroll-fading.md`,
`.claude/rules/motion.md` and the project's style guide sections on motion,
tables and scrollbars first. Then read the page, the app shell and layout
components, the table and pager components, and any `onScroll`, `scrollTo`,
`scrollIntoView`, `scroll-snap`, `sticky` or `IntersectionObserver` code it
touches.

1. **Scroll triggers nothing.** List every element that appears, moves or
   changes with scroll position. Each one is a finding.
2. **No scrolljacking.** No snapping, and no scroll the person did not cause.
3. **Refetches and polls** leave the rows in place, with no fade and no jump.
4. **More is obvious.** The pager states the range. Sideways table scroll shows
   a cut-off column. There is no empty band that looks like the end.
5. **Above the fold** at a typical desktop height: the title, tiles, any
   warning panel and the first rows.
6. **Scroll regions** use the project's styled scrollbar, and a workspace page
   fills the viewport and scrolls its regions instead of the page.
7. **Photos** hold their size while loading and say so in words when they
   fail.
8. **Accessibility.** Nothing is hidden from the screen reader until scrolled
   to, and 200% zoom clips nothing.

Report findings as: what happens, which rule it breaks (with its NN/g source),
and the fix. Do not change code unless asked. When fixing, run the project's
lint, typecheck and build, and say plainly if it has not been tried in a
browser.
