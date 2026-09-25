# Colour use — why the palette is small, and how to argue for a change

Applies to **any decision about which colour something gets**, and to any
proposal to add, change or reuse a colour. Source:
[Using Color to Enhance Your Design](https://www.nngroup.com/articles/color-enhance-design/)
(Nielsen Norman Group).

`colour-type-icons.md` decides whether a colour can be **read**. This file
decides whether a colour should be **used** at all, with the NN/g reasoning to
point to. Values stay in the project's design system / style guide doc (e.g.
`DESIGN.md`) and theme config. This file names no hex code.

## The palette, read through NN/g

- **The harmony is monochromatic.** One brand hue in a few steps (base, bright,
  deep, soft), on a neutral ramp chosen to match it. NN/g calls a monochromatic
  scheme the easiest to keep coherent. That is why the neutrals share the
  hue's temperature: a warm grey beside a cool blue adds a second temperature,
  which is a second design.
- **Three colour jobs, not three hues.** NN/g advises starting with two or three
  colours so the hierarchy stays clear:
  1. **Neutral**: the canvas, cards, words, lines, and any deep navigation
     panel.
  2. **Accent**: "you can act on this", and the current page.
  3. **Status**: success, warning, danger, info. They are used only to report a
     state.

  Charts are a fourth job, and it is fenced: chart colours appear only inside a
  chart, never as text, a status or a control. Any other new job is refused
  unless the style guide changes first.
- **Status hues are not a harmony choice.** Green, amber and red must stand out,
  and because they are rare, standing out still works.
- **Follow the brand guideline.** A fixed guideline makes decisions easier. The
  theme config is where it lives in code.

## 60 / 30 / 10

NN/g's ratio is the colour budget:

| Share | NN/g | Typically |
|---|---|---|
| 60% | dominant colour | the work: surface cards on the canvas, ink, lines |
| 30% | secondary colour | the navigation panel or another secondary surface |
| 10% | accent, for the main action | the current page, the primary button, actionable counts |

- **Measure the area**, from a screenshot, not by counting classes.
- **Fix a failing screen by demoting**, never by adding a colour.
- **Status colour spends from the 10% too.** A table where every row is red has
  no signal left. A stat tile takes a danger or warning tone only when the
  figure is non-zero.

## Use a colour the same way everywhere

NN/g: a colour that marks the action on one screen must mark it on every
screen. Frequent users scan the same screens many times a day and learn by
position and colour.

- The accent means **"you can act on this"**. It is never a status, a decoration
  or a heading. The accent link and the accent button are the same promise.
- Success, warning and danger mean the same state on every screen. Use one
  shared status component and its tones.
- **One colour, one meaning.** If a new use would give a colour a second
  meaning, the new use needs a neutral and a word instead.
- **The soft accent means "this one is open or chosen"** (the drill-down row, the
  selected timeline row). It never means a status.

## Colour meaning is assumed, not known

NN/g: little research shows a universal emotional effect of a colour, and
meanings differ between cultures.

- **Never rely on colour to explain.** Every state carries a word.
- **The status mapping (green good, amber caution, red problem) is an
  assumption.** Record it as untested with the real audience until someone has
  tested it.
- **Do not give a colour a cultural or emotional job.** Meaning comes from the
  word.

## Testing a colour decision

1. **Contrast, measured** on the ground the colour actually sits on. Record the
   ratio in the style guide beside the token.
2. **Colour blindness**: check the screen in a greyscale or deuteranopia
   emulation (Chrome DevTools, Rendering). Each state must still read.
3. **On an ordinary monitor**, not only a calibrated one.
4. **With the real audience, when possible.** Until then, say in the change that
   it has not been tried with them.
5. **Change the style guide and theme config together**, and any sibling
   product's files too for a shared value.

## Checklist (every colour decision)

- [ ] The colour does one job: neutral, accent, status, or chart inside a chart
- [ ] No new hue. A new state got a neutral and a word
- [ ] The colour means the same thing here as on every other screen
- [ ] The screen still passes 60 / 30 / 10 by area
- [ ] Nothing relies on colour alone, or on a cultural reading of a colour
- [ ] Contrast measured on the real ground, and checked in greyscale
- [ ] "Untested with the audience" stated where it applies
