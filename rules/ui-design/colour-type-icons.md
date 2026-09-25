# Colour, type and icons — whether it can be read

Applies to **every class that sets a colour, a font size, or draws an icon**.
`ui-workflow.md` decides what is loud. This file decides whether it can be read
at all, on a cheap monitor, all day. Concrete values below are examples; use
your project's tokens.

## Colour

- **Tokens only.** Every colour comes from the theme config. These are defects:
  an arbitrary value (`bg-[#...]`, `text-[rgb(...)]`), a framework default grey,
  and an inline `style` colour. Third-party widgets (e.g. a map library) are
  styled once in a stylesheet.
- **Text 4.5:1. Large text (18px+ bold, 24px+) and meaningful icons 3:1.**
  Measure against the ground it actually sits on. Canvas, sunken and status
  backgrounds all lower the ratio.
- **The muted ink token is the lightest text, placeholders included.** A heavy
  line token is a border or a disabled glyph, never words. Do not add a lighter
  grey.
- **On a dark navigation panel, set a higher floor** (e.g. 5:1). Opacity is a
  way to write the value, not a licence to dim it.
- **Status: fills are for shapes, words take the dark step.**

  | Status | Dot / bar / shape | Words and icons | Pill background |
  |---|---|---|---|
  | Success | `success-fill` | `success` | `success-bg` |
  | Warning | `warning-fill` | `warning` | `warning-bg` |
  | Danger | `danger-fill` | `danger` | `danger-bg` |
  | Info | `info-fill` | `info` | `info-bg` |

  Never set text in a fill token. Use one shared status pill that already pairs
  these. A warning fill is never a mark on its own. It sits beside its word.
- **The accent is the link colour.** The info colour is never used for a link.
  A table's row subject is an underlined ink link.
- **Chart colours are never text and never a status.** Where a series sits beside
  a button, start the ramp one step in so it does not match the accent.
- **Colour is never the only signal.** A state also carries a word, an icon or
  a letter. Some users are colour-blind.
- **A new state gets a neutral and a word, not a new hue.**
- **Hairlines separate. They do not outline controls on their own.** Inputs
  take a line token, and a stronger one on hover.
- **The focus ring is ink**, 2px with a 2px offset. It is never the accent,
  and never removed without a replacement. **On a dark navigation panel it is
  white**, offset against the panel, because an ink ring disappears on dark.

## Type

- **Type tokens only**: a named ramp (e.g. caption 12, label 13, body 14,
  subheading/prose 16, heading 20, title 24, display 30). No arbitrary pixel
  sizes, and no framework default size classes in new code.
- **12px is the floor.** An exception is a marker rather than something to read.
- **The body size (e.g. 14px) is the default.** Reach for anything else only
  with a reason.
- **Hierarchy by size, then weight, then lightness.** Inside body, use a
  medium weight and secondary/muted ink, not a new size.
- **Use a token as it is.** A token plus a leading or tracking override is a new
  style in disguise.
- **Uppercase is for the overline style only**: table column headers and card
  eyebrows. Group labels and section headings are sentence case.
- **`tabular-nums`** on any column or list of figures (counts, times, amounts),
  so the digits line up.
- **Text wraps or truncates on purpose.** A truncated value carries its full
  text in `title` or is readable elsewhere. No fixed-height text container
  clips at 200% zoom.
- **Prose keeps a 40–60 character measure.** Table cells are exempt.

## Icons

Source: [Icon Usability](https://www.nngroup.com/articles/icon-usability/)
(NN/g). Only a few icons are universally understood (home, search, print).
Everything else needs its word: "a word is worth a thousand pictures".

- **One icon module only.** Stroked, `currentColor`, one stroke width, round
  caps. No second icon library, no filled family, no pasted SVG in a page.
- **If a glyph is missing**, add it to the icon module on the same grid and
  stroke. If iconscout is used as a fallback, pick a stroked, single-colour icon
  that matches, and ask before downloading anything.
- **Sizes**: 16px inline with body text, 20px in an empty-state circle (examples).
- **One glyph, one meaning.** Search the icon files for the concept before
  adding a second glyph for it.
- **A visible label beside the icon by default.** Icon-only is allowed for
  universally understood actions (close, overflow, sort, password reveal,
  collapsed navigation, map transport and zoom controls), and it always carries
  an `aria-label`. **A tooltip is not the label.** Collapsed navigation earns
  its exception because its flyout shows the words on hover and on Enter.
- **Simple and schematic**, not realistic. **The 5-second rule**: if the
  meaning of a glyph takes more than five seconds to work out, it needs a
  different glyph or only a word.
- **Icons shrink in salience on a desktop.** Do not rely on an icon to be
  noticed on a wide page. The word and the position do that work.
- **A new or unusual glyph is tested** for recognition with users, or the
  change says it was not.
- **Decorative icons take `aria-hidden="true"`.**
- **Pad the target, not the glyph.**

## Checklist

- [ ] No hex or arbitrary colour, no default grey, no arbitrary font size
- [ ] No text below 4.5:1 on its real ground, and nothing below 12px
- [ ] No text in a fill token, no info-coloured link, focus ring is ink
- [ ] Every state has a non-colour signal
- [ ] Figures use `tabular-nums`, text survives 200% zoom
- [ ] Icons from the one icon module, labelled or hidden as appropriate
