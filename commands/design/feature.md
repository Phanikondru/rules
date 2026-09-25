---
name: feature
description: Audit a feature that ships, or ideate one that does not — the goal it serves, what it costs the screen, and the cheapest form that shows it, written so a designer can build from it (NN/g: user goals over features, feature richness, context architecture)
---

The feature is `$ARGUMENTS`. Read `.claude/rules/feature-value.md` first, then
`.claude/rules/ui-workflow.md`, and the project's style guide overview plus
the sections the feature touches or would touch.

**Pick the mode from `$ARGUMENTS`.** If it names something in the code (a
page, a component, a route), it is **Mode A**. If it names a wish, a problem or
a request, it is **Mode B**. If it could be either, say which you took and why,
in one line, and carry on. Do not ask first.

This command does not write code. It ends by pointing at `/spec` and `/ui`.

---

## Mode A — a feature that already ships

### 1. Read it

- The page, its route, the components, hooks and API calls it uses, and its
  copy strings.
- What the style guide says about it, and whether the entry is complete
  (`style-guide.md`).
- The backend for what the API actually returns, before assuming a shape.
- Run it if you can (`/run`, or the Chrome tools). Otherwise say the read was
  from the code.

### 2. State the goal it serves

Write the rule 1 sentence for it, from the evidence in the code rather than
from the ticket that built it. Then say honestly whether the feature serves
that goal, partly serves it, or serves a different one.

### 3. Name what matters on it

The one decision the screen exists for, what leads, what supports, and what is
noise. Then read `feature-value.md` rule 6: what context sits beside each
figure, what is missing that would change the reading, and what is there that
changes nothing.

### 4. Count what it costs

Rule 3's six costs, against the screen **as it is today**. Include the states
a screenshot hides: loading, empty, error, permission denied, a zero, a long
name in the users' own script, a hundred rows.

### 5. Show the ways it could be shown instead

Two or three forms from rule 8, cheapest first. For each: what it would look
like in this system by component name, what it costs, and what it gives up.
Recommend one, or recommend leaving it as it is — that is a real answer, and
it is the right one when the feature already fits.

Check rule 4 before proposing anything new: is this a findability problem, a
value the API already returns, or a shared component that could be extended?

### 6. Report

- **What it is today**, in one paragraph, in the users' words, with every
  element named by its `style-guide.md` name.
- **The goal**, and whether it is served.
- **What matters, and what is noise.**
- **The cost**, plainly.
- **The ways**, with one recommendation in one sentence and the rejected
  options at one line each.
- **Findings**, if any, as `file:line` + what the person experiences + the rule
  or style-guide section broken + the fix.
- **What was not checked**, and what only the business can answer.

A feature that is fine is reported as fine. Do not invent findings, and do not
propose a rebuild of something that works.

---

## Mode B — a feature that does not exist yet

### 1. Name the goal, not the feature

Write the rule 1 sentence. If the request cannot be said without its own name
in it, say so and ask what the person does today instead. **Ask rather than
guess anything that is a business rule** (who may, how long, what counts as
valid). Those belong to the backend.

### 2. Say how we would know it worked

One observable change. If it can only be seen by watching a user, say that,
and say nobody has yet.

### 3. Check it is not already answered

Walk rule 4 in order: already there but unfindable, a value the API already
returns, a shared component extended, or genuinely new. Check the component
folders and the copy files for an existing word for this thing before
inventing one. Check the backend for whether the data exists at all.

If the answer is "it already exists", stop there and say where.

### 4. Ideate three shapes

Rule 9. For each shape:

- **The form**, by component name from rule 8 and the style guide.
- **Where it lives**: the navigation group, page, card, row, sheet or dialog,
  and the answers to rule 5's four questions (structure, name, noun, what
  persists).
- **A sketch in words** at the real content — a long name, a zero, a hundred
  rows — and the empty, loading, error and permission-denied states.
- **What it costs**, from rule 3.
- **What it gives up.**

Then **recommend one in a single sentence**, and say why the other two lose.
Where the choice is contested, name the UX law that settles it (`/why`).

### 5. Name the slice that ships on its own

The smallest version that is useful by itself, and what is deliberately left
out of it. Say what would come next only if the first slice earns it.

### 6. Report

- **The goal**, and what happens today.
- **How we would know it worked.**
- **Whether it already exists** in some form.
- **Three shapes**, then the recommendation.
- **The first slice**, and what is out of it.
- **What goes into the style guide** (reusable) and what stays in the PR (this
  screen only), per `style-guide.md`.
- **Reference-product examples** — three or more products — for anything the
  style guide does not cover, taking the structure and not the skin.
- **Open questions** only the business or the backend can answer, listed
  rather than guessed.
- **Untested with users**, stated.

---

## After either mode

Say which command comes next: `/spec` to write it down before it is built,
then `/ui` to build it, `/why` if a choice is still contested, and `/ux-audit`
if the screen around it needs a full pass. Do not start building in this
command.
