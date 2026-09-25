---
name: ideate
description: Generate feature and improvement ideas for a screen, or learn from someone else's solution — the person's question, what the screen flattened, abstraction, How Might We questions, eight or more ideas, three shapes, then the constraints (NN/g: ideation, How Might We, functional fixedness, jobs to be done, parallel design)
---

The subject is `$ARGUMENTS`. Read `.claude/rules/ideation.md` first, then
`.claude/rules/feature-value.md`, `.claude/rules/ui-workflow.md`, and the
project's style guide overview and the sections the subject touches.

**Pick the mode from `$ARGUMENTS`.**

- **Mode A: a screen or feature that ships** (a page, component or route).
  Find what could be better.
- **Mode B: a problem or wish** with no screen yet. Find what could exist.
- **Mode C: a solution somebody else made** (a teammate's branch, a
  competitor's screen, a reference-product flow). Understand why it works, then
  decide whether it fits.

If it could be more than one, say which you took and why in one line, and carry
on. Do not ask first.

This command does not write code. It ends by pointing at `/feature`, `/spec`
and `/ui`.

---

## 1. Read the real thing

- **Mode A and C**: the page, its route, the components, hooks and API calls,
  the copy strings, and what the style guide says. For a teammate's work, read
  the diff or branch. Run it if you can (`/run`, or the Chrome tools),
  otherwise say the read was from the code.
- **All modes**: check the backend for what data exists before imagining a
  shape that needs data that does not.
- Say plainly what does not exist yet. Do not invent it.

## 2. The person's question

Write it in the users' words (rule 1): "Where was he, in what order, for how
long?" Then list what the person does today to answer it, including every
workaround. If there is no evidence of a workaround, say so.

## 3. Run the lenses

First list the **parts** of the screen (for a map page: the list, the map, the
detail or timeline, the header controls). Then fill a **coverage grid**: every
part against rule 2's eight lenses (time, direction, change, comparison, cause,
absence, uncertainty, next step). Each cell is one line: what the part shows
today, what was lost, and whether it matters to the question, or "nothing
found". **An empty cell is a skipped lens and is not allowed.** A part that
looks finished, or is well specified in the style guide, still gets its row: a
detailed spec is not proof nothing was flattened.

The user often cannot know what is possible, so the grid is where ideas come
from. Check the type definitions and the backend for fields the screen does not
use yet, and treat each unused field as a candidate idea.

**Mode C only**: also name which lens the other solution used, what problem it
solved, and what it costs (data, motion, states, maintenance). This is the
step that turns "they built playback" into something reusable.

## 4. Abstract

Strip the nouns and restate the problem (rule 3). Name one or two distant
fields that solved the same structure, and the mechanism each uses. Bring back
the mechanism only.

## 5. How Might We

Three to five questions (rule 4). Check each against the list: from a finding,
an outcome, positive, broad enough, no solution inside.

## 6. Diverge

At least **eight ideas**, one line each, without judging (rule 5). Include:

- a subtraction, or leaving it as it is,
- the cheapest form (a cue, a column, a line in a sheet),
- one idea the rules would probably reject,
- **at least one idea per part** from the grid, so the list is not all about the
  loudest finding.

Group the ideas by the person's goal and mark the cheapest first. **An idea
that hits a rule stays on the list**: say what it needs (a style-guide
decision, a new API field) or how it is reshaped. Never leave it out because
it might be rejected.

Set the first idea aside and say what it was.

## 7. Converge into three shapes

Cluster the ideas and pick three that differ in kind, not in polish. For each,
in the terms of `feature-value.md` rule 9: the form by component name,
where it lives, a sketch in words at real content (a long name in the users'
own script, a zero, a hundred rows), the four states, what it costs, and what
it gives up.

Recommend **one in a sentence** and say why the other two lose. Name the UX law
that settles it if the choice is contested (`/why`).

## 8. Check the constraints, after the idea

In rule 7's order: honesty, the API, the style guide and the rules, reading and
density, where it lives. For each failing point, say whether the idea is
reshaped or sliced. Never drop an idea silently because it hits a rule.

If it needs a pattern the style guide does not have, say reference products
come first (three or more, structure not skin) and the entry goes into the
style guide in the same commit.

## 9. Name the first slice

The smallest version that ships alone and answers the person's question, and
what is deliberately left out. Say what would come next only if it earns it.

## 10. Report

- **Mode and subject**, in one line.
- **The person's question**, and what they do today.
- **What was flattened**, as the coverage grid (parts by lenses).
- **Coverage**: one line naming the parts and lenses covered, and anything not
  looked at.
- **The abstraction**, and the field borrowed from.
- **How Might We questions.**
- **The ideas**, as a list.
- **Three shapes**, the recommendation, and the rejected two.
- **Constraints hit**, and how each was resolved.
- **The first slice.**
- **For Mode C**: what to keep from the other solution, what to change, and
  what it would cost.
- **What was not checked**, and what only the business or the backend can
  answer.
- **Untested with users**, stated.

Do not invent findings. If the screen already serves the person's question,
say so and stop, but only once the coverage grid is complete and every part
has been checked.

---

## After the report

Point at the next command: `/feature` to judge whether it earns its place,
`/spec` to write it down, `/ui` to build it, and `/ux-audit` for a full pass on
the screen around it.
