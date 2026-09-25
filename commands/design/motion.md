---
name: motion
description: Add or review a transition or animation against the project's motion rules (Zajno's eight techniques, NN/g's purposes of animation, the style guide's motion section)
---

The motion change is `$ARGUMENTS`. Read `.claude/rules/motion.md` and the
motion section of the project's design system / style guide doc (e.g.
`DESIGN.md`) first. For the eight techniques and their implementation, use the
`motion-design` skill (`skills/motion-design/SKILL.md`). Then read the theme
config (durations, curves, keyframes), the reduced-motion block in the global
stylesheet, and any component the change touches.

1. **Name the job**: confirm a response, show where something came from, or
   show a state change. If it has none, the answer is no motion.
2. **Check it is on the "may move" list** and uses a technique `motion.md`
   allows. Anything else needs a style-guide entry first, so write that entry
   before any code.
3. **Check the fixed limits**:
   - duration tokens only
   - curve tokens only
   - no springs, no content stagger, no scroll-driven motion, no scale or shadow on hover
   - fade once, never on a refetch
4. **Tokens, not arbitrary values.** A new duration, curve or keyframe goes
   into the style guide and theme config, never an arbitrary value in a
   component.
5. **Reduced motion**: confirm the global block covers it, and that nothing is
   lost with motion off.
6. **Signifier check**: the entry direction must not promise a drag that does
   not exist (`interactions.md`, rule 2).

When building, run the project's lint, typecheck and build. Report the
`motion.md` checklist, and say plainly if it has not been seen in a browser
with reduced motion on and off.
