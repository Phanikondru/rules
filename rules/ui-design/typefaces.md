# Typefaces — one family, roles by weight, and what a second one would need

Applies to **any decision about a typeface**: adding, replacing or pairing one,
and any change to a `font-family`, `@font-face` or font weight. Source:
[The Dos and Don'ts of Pairing Typefaces](https://www.nngroup.com/articles/pairing-typefaces/)
(Rachel Krause, NN/g, 2022).

`colour-type-icons.md` decides the size tokens and `visual-design.md` §9 names
the typographic terms. The project's design system / style guide doc (e.g.
`DESIGN.md`) records the face and why it was chosen. This file decides **whether
a second face may exist, and how hierarchy is made without one**.

## What the research found

NN/g's five guidelines:

1. **Support multiple languages.** Test a face in every language the product
   shows before choosing it. A missing character set breaks the design for
   those readers.
2. **Run the 1Il test.** The numeral `1`, capital `I` and lowercase `l` must
   look different. It matters most in finance, government and healthcare,
   where people read and copy alphanumeric codes.
3. **Mix decorative with neutral, and less is more.** A personality face
   belongs in a header or an illustration, never in body copy. Pair intense
   decoration with a plain sans-serif.
4. **Use contrasting weights.** One family in several weights looks
   professional, and weight sets the hierarchy that guides the eye.
5. **Give each face one role.** Two faces for body copy make a design look
   inconsistent and unrefined, and cost trust. A style guide keeps it so.

A tool for people reading dense records or codes sits at the plain end of this
advice on purpose: a pairing is a cost with no task it serves.

## Rules

### 1. One family

- **One family only**, shared across the product family. No second
  `font-family` in a component, a page, a chart, a map label or a print style.
  A logo drawn as outlines is not text the person reads and may be the one
  recorded exception.
- **Long prose uses the same family at the prose size**, never a serif "for
  reading".
- **No decorative, script, display or monospaced face.** Figures use
  `tabular-nums` instead of a monospaced face (`visual-design.md` §9).
- **Fallbacks are system sans-serif** (`ui-sans-serif`, `system-ui`), never a
  serif or a monospace stack.

### 2. Hierarchy is weight, then size, then lightness

- **Weight is the first tool.** A heading that differs from body by size alone
  is a finding. Size steps are from the ramp (`colour-type-icons.md`).
- **Weights are contrasting, not adjacent.** 400 beside 500 inside body is a
  quiet emphasis. A role that must stand out takes 600 or 700.
- **Never fake a style.** No synthetic bold, and no italic for emphasis
  (`visual-design.md` §9). If a weight is not loaded, it is loaded properly or
  not used.
- **Load only what is used.**

### 3. Every language is tested

- **Any new string type is checked in every supported script as well as
  English**: a place name, a body of free text, a person's name. Line height
  stays on the token, because a tighter override can clip vowel signs and
  diacritics in some scripts.
- **A face that lacks a script is not added**, however good it looks. The
  browser's fallback face would mix two designs in one line.

### 4. Codes must be readable

- **Run the 1Il test on any face or weight change.** Type `1 I l 0 O` in a
  field and in a table cell at body size, and look.
- **A number a person reads or copies** (permit, vehicle, phone, reference
  number) is set in the family with `tabular-nums`, at body size or larger,
  never in caption and never in a light weight.
- **Do not add a face to "fix" a code.** Change the size, the weight or the
  grouping (phone numbers in chunks, the `ux-laws` skill Chunking).

### 5. A second face needs a reason and a decision first

A second family is not banned by taste. It is refused until a task cannot be
done without it. If one is proposed:

1. **State the job** it does that the first family cannot, and the role it will
   hold. "Looks better" is not a job.
2. **It has one role**, never body copy, and never the same role as the first
   family.
3. **It supports every needed script and passes the 1Il test**, or it is used
   only for text that never needs those scripts and is never a code.
4. **It is loaded with the app**, not from a third-party font service, and its
   weights are all real.
5. **If it is a shared brand value**, the change is made in every product that
   shares it in the same pass.
6. **The style guide changes first**, with the reason and the rejected options
   recorded, and the config and guide agree.

Until all six are written, the answer is no.

## Checklist (every font or type-role change)

- [ ] Only the one family is in use, with system sans-serif fallbacks
- [ ] No decorative, script, display, serif or monospaced face anywhere, charts and maps included
- [ ] Hierarchy comes from weight first, with size steps from the ramp, and no faked bold or italic
- [ ] Every weight used is loaded, and none is synthesised
- [ ] Checked in every supported script as well as English, with line height on the token
- [ ] The 1Il test passes, and codes are `tabular-nums` at body size or larger
- [ ] Any second face has a job, one role, script coverage, local files, a shared change where needed, and a style-guide entry first
