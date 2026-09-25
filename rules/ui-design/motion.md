# Motion — when something moves, and why

Applies to **every transition and animation**: hover and focus colour, dropdowns,
dialogs, sheets, navigation width, skeletons and spinners. Sources:
[Motion Design Principles](https://motion.zajno.com/) (Zajno, eight techniques)
and [The Role of Animation and Motion in UX](https://www.nngroup.com/articles/animation-purpose-ux/)
(NN/g). The eight techniques themselves, and how to implement them, are in the
library skill `skills/motion-design/SKILL.md`; this file does not repeat them.
Values and the settled list of what moves live in the project's design system /
style guide doc (e.g. `DESIGN.md`) and theme config. This file decides which
technique a new motion may use.

## What motion is for

Motion has three jobs. A movement that does none of them is removed.

1. **Confirm a response**: hover, focus, pressed.
2. **Show where something came from**: a sheet from the right, a dropdown from
   its trigger.
3. **Show a state change**: a caret rotating, a disclosure opening, a
   navigation panel narrowing.

It is never decoration in a tool that is operated rather than watched.

### NN/g's five purposes

| Purpose | Guidance for a working tool |
|---|---|
| **Feedback** | Yes: colour on hover, focus and press |
| **State change** | Yes: caret, disclosure, skeleton to content |
| **Navigation** | Narrow: a sheet's slide and an overlay fade. No page transitions |
| **Signifier** | Careful: the entry direction must not promise a drag that does not exist |
| **Attention** | No: no pulsing badge, flashing row or animated counter |

- **One thing moves at a time.**

## Microinteractions

NN/g ([Microinteractions](https://www.nngroup.com/articles/microinteractions/))
defines one as a trigger paired with a small, targeted response in context.
Typical ones:

| Trigger | Feedback |
|---|---|
| Pointer over a control | Colour change at the hover duration |
| Opening a dropdown or disclosure | The caret rotates |
| Clicking a column header | The sort caret changes direction |
| Starting a request | A spinner replaces the glyph, and the label stays |
| Toggling a password reveal | The glyph swaps, and the label says what the next click does |
| A count changing elsewhere | The badge count changes (a system trigger) |
| Narrowing the navigation | Its width moves at the panel duration |

- **Each one shows status or prevents an error.** None is decoration.
- **Brief and subtle**: it never loops, except a spinner while work runs.
- **The states are clearly different** at rest and after, even with motion off.
- **The brand shows as restraint** in a serious register. No hearts, confetti or
  bounce.
- **Live requirement feedback** (such as password rules) shows only rules the
  server has stated, never rules the client has made up.

## Fixed limits

- **A small set of durations**, as tokens (e.g. hover 120ms, panel 160ms,
  overlay 200ms).
- **A map or canvas library's own animation** may take its own duration if it
  carries information ("you were there, you are now here"). A second such case
  goes back to the style guide first.
- **A small set of curves**: one for a state that toggles, one for arriving
  (ease out), one for leaving (ease in). No springs, bounce or overshoot.
- **Loops are slower on purpose**: skeleton sheen about 1.6s, spinner about 1s.
  Do not make them "consistent" with the transitions.
- **Prefer CSS.** Add an animation library only by a recorded decision.
- **Reduced motion is honoured globally** in one place. A new keyframe must be
  covered there.
- **Motion never carries meaning alone.**
- **Nothing waits on an animation.** Content is readable and clickable at once.
- **A new duration, curve or keyframe** goes into the style guide and theme
  config first, never as an arbitrary value in a component.

## What may move, and what may not

**May**: colour on hover and focus, a caret rotating, a popover, dialog or
sheet entering, a skeleton shimmering, a spinner turning, a disclosure opening,
a navigation panel's width when the person toggles it.

**May not**: table rows on load, numbers counting up, anything entering on
scroll, page transitions, nav items arriving one by one, and shadows or scale on
hover.

## The eight techniques in a working tool

See `skills/motion-design/SKILL.md` for each technique. In an operated tool the
default stance is: easing and fade **used**; offset/delay only for a skeleton
sheen, never a content stagger; transform/morph narrow (a caret, a spinner
replacing a glyph); zoom, masking, dimension and parallax **not used**.

- **Entering eases out, leaving eases in.**
- **Fade once.** Never on a refetch or a re-render.
- **A skeleton's column delay is not a stagger.** It is one light crossing one
  surface.

## Checklist (every motion change)

- [ ] The movement names its job: confirm, show where, or show a state change
- [ ] It is on the "may move" list, with a technique this file allows
- [ ] Tokens only for duration and curve
- [ ] No springs, no stagger, no scroll-driven motion, no scale or shadow on hover
- [ ] Reduced motion covered globally, and nothing lost with motion off
- [ ] Any new token written into the style guide and theme config
