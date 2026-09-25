---
name: motion-design
description: UI motion/animation principles (easing, offset & delay, fade, transform & morph, masking, dimension, parallax, zoom) and how to apply them with framer-motion in a design-system-consistent, accessible way. Use whenever adding or reviewing entrance animation, hover motion, scroll-reveal, page transitions, or any interface movement — not just on marketing pages. Pairs with ui-ux-principles (accessibility/perf) and ux-laws (why a static choice is right or wrong).
---

# Motion Design

Motion is a fourth design layer alongside color, type, and spacing — it directs
attention, conveys hierarchy, and signals causality (this happened *because*
of that). Used well it's invisible; used badly it's the first thing anyone
notices. Treat every animation as a deliberate design decision with a named
justification, the same discipline `ux-laws` asks for static layout.

> Source: [motion.zajno.com](https://motion.zajno.com/) (Zajno Digital
> Studio) — 8 named techniques, itself an evolution of Disney's classical
> animation principles applied to UI.

## The 8 techniques

1. **Easing** — speed varies over the course of a movement (linear, ease-in,
   ease-out, cubic). Nothing in the real world moves at constant velocity;
   linear motion reads as robotic. Ease-out (fast start, slow settle) is the
   default for anything entering the screen — it reads as arriving with
   intent. Ease-in (slow start, fast exit) suits things leaving.
2. **Offset & delay** — stagger related elements instead of moving them as
   one block. A list that reveals item-by-item with a small per-item delay
   reads as considered; the same list appearing all at once reads as a
   flash. Keeps hierarchy: what matters most can lead.
3. **Fade in/out** — opacity transitions for appearance/disappearance. The
   cheapest, safest motion — pairs with almost every other technique rather
   than standing alone (e.g. fade + rise, fade + scale).
4. **Transform & morph** — one shape becomes another while keeping visual
   continuity (an icon becoming a checkmark, a button becoming a card). Tells
   the user "this is still the same object, just in a new state" — stronger
   than a hard cut for state changes.
5. **Masking** — a shape acts as a container/window; content moves or reveals
   within it (text sliding up inside a fixed-height clip, an image revealed
   by an expanding mask). Reads as premium because it implies depth without
   claiming a full 3D scene.
6. **Dimension** — depth cues (shadow shift, scale, subtle 3D tilt) that make
   flat UI read as layered/floating. Use sparingly — this is the effect
   DESIGN.md's "composited dashboard mockup" pattern already leans on
   (offset, rotated panels + shadow, see `DashboardMockup.tsx`).
7. **Parallax** — layered elements move at different speeds along an axis,
   implying depth as the viewport scrolls. Powerful on a marketing hero,
   actively harmful in a dense data table — reserve for low-density,
   high-emotion surfaces only.
8. **Zoom** — transition between two interface states by continuously scaling
   through the space between them (a card expanding into a detail view)
   instead of cutting. Preserves spatial context; the user never loses track
   of "where did that go."

**Real-time vs not-real-time** — real-time interfaces respond *during* the
interaction (drag, hover-follow, live slider feedback); not-real-time
interfaces respond *after* it completes (a click triggers a 300ms
transition). Most UI motion is not-real-time — reserve real-time response for
genuinely continuous input (drag handles, scrubbers), not clicks and taps.

## Applying this with framer-motion (already installed)

This codebase already has a house style — reuse it rather than inventing new
timing per component:

- **Entrance pattern** (seen in `HeroBand.tsx`, `KpiTile.tsx`):
  `initial={{ opacity: 0, y: 6 }} animate={{ opacity: 1, y: 0 }} transition={{ duration: 0.28–0.32, ease: [0.2, 0, 0, 1] }}`
  — a small rise + fade, the house easing curve. Don't invent a different
  curve for a new component without a reason.
  ⚠️ **But drop the `opacity: 0` half of this pattern for anything that can
  be above the fold or visible on first paint** (a hero, anything using
  `whileInView` instead of `animate`). `opacity: 0` on `initial` ties
  visibility to framer-motion resolving the animation on the JS main
  thread — under real contention (a busy tab, a slow device, heavy
  hydration) that resolution can lag seconds behind mount, and was
  reproduced live on this project's landing page: a near-invisible page
  for several seconds on every load, not a one-off. Animate `y` only for
  first-paint content — worst case then degrades to "fully readable,
  slightly offset," never to "invisible." Reserve the opacity fade for
  content that's already confirmed off-screen at mount (scroll-reveal
  further down a long page), where the animation has a full scroll's worth
  of time to resolve before a user could see it stuck.
- **Named duration/easing tokens** already exist in `apps/web/src/index.css`
  (the "Defensible Intelligence" timing system): `--duration-micro` 120ms
  (hover/focus/color), `--duration-small` 200ms (dropdown/tooltip/chip),
  `--duration-medium` 320ms (modal/sheet/section enter), `--ease-entrance`
  `cubic-bezier(0.2, 0, 0, 1)`, `--ease-standard`
  `cubic-bezier(0.4, 0, 0.2, 1)`. Map technique → tier: micro-interactions
  (hover, focus) → `--duration-micro`; a dropdown/menu opening → `--duration-small`;
  a section/card/modal entering → `--duration-medium` / `--ease-entrance`.
- **Stagger** (offset & delay) via a `delay` prop threaded per item —
  `KpiTile` already does this (`delay={i * 0.05}` pattern at call sites).
  Keep the per-item delta small (40–80ms) — large gaps read as slow, not
  considered.
- **Scroll-triggered reveal**: use framer-motion's `whileInView` +
  `viewport={{ once: true, margin: '-80px' }}` rather than a raw
  IntersectionObserver — `once: true` so re-scrolling past a section doesn't
  replay it (replaying on every scroll reads as broken, not polished).

## Accessibility — non-negotiable

- Respect `prefers-reduced-motion`. This codebase already sets a global CSS
  override (`index.css` `@media (prefers-reduced-motion: reduce)`) that zeroes
  transition/animation durations, and components add `motion-reduce:` Tailwind
  variants for hover states. **framer-motion animations are not covered by
  that CSS media query** — a `motion.div` with `animate` props still runs
  under reduced-motion unless you explicitly gate it. Use framer's
  `useReducedMotion()` hook (or wrap the tree in `<MotionConfig reducedMotion="user">`)
  so entrance/scroll animations collapse to an instant appearance, not just a
  faster one.
- Never animate anything load-bearing for comprehension on its own — motion
  is a hierarchy/delight layer, the static end-state must be fully legible
  with zero animation.
- Don't animate on every scroll tick for content already read (see `once: true`
  above) — that's the single most common "cheap-feeling" motion mistake.

## When NOT to animate

- Dense data tables and financial figures — this codebase's own binding rule
  (`ui-quality-bar.md` / `DESIGN.md`) is "tables intentionally use no motion
  (they are reading tools)." Motion competes with scanning.
  DataTable/financial-grade surfaces stay static.
- Anything already fast (<100ms) — animating it just adds latency the user
  feels as lag, not polish (Doherty Threshold, `ux-laws`).
- Don't animate the same technique twice in one view for two different
  reasons — if fade-in-on-scroll and hover-lift are both present on a card,
  make sure they're solving different problems (entrance vs. affordance),
  not fighting each other.

## Output discipline

- Name the technique used and why, the same way `ux-laws` names a law —
  "offset & delay on the stat tiles, so the four numbers don't all land as
  one flash" beats "added a stagger, looks nicer."
- Reuse the project's existing duration/easing tokens before adding a new
  curve. A new curve needs a stated reason (different tier, different
  surface) — not a preference.
- Ship reduced-motion handling in the same change, not as a follow-up.
