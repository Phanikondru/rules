# Feature value — the goal a feature serves, what it costs, and where it is shown

Applies to **every request for something new** (a page, a screen, a tab, a
column, a tile, a filter, a badge, a setting, an export) and to **every review
of something that already ships**. It runs before `design-specs.md`, which
writes the spec, and before `ui-workflow.md`, which builds the screen. Sources
(NN/g):
[Stop Obsessing Over Features: Focus on User Goals](https://www.nngroup.com/videos/stop-obsessing-over-features-focus-on-user-goals/)
(Rachel Krause, 2022) ·
[Feature Richness and User Engagement](https://www.nngroup.com/articles/feature-richness-and-user-engagement/)
(Jakob Nielsen, 2007) ·
[Context Architecture](https://www.nngroup.com/articles/context-architecture/)
(Paz Perez, 2026).

the `ux-laws` skill names the law behind a decision. `ui-workflow.md` decides how a
screen gets built. This file decides **whether the thing should exist at all,
which form is the cheapest one that does the job, and where on the screen it
belongs** — and it is the file to argue from when the answer has to be
explained to somebody else.

**On the third source.** *Context Architecture* is written about AI systems:
the layers of instruction, retrieval and memory an agent reasons inside. What
is taken from it here is the half that is information architecture —
structure, findability, mental models, memory, and the claim that **"context is
never neutral"**. Its other half (skills, tools, retrieval) is not about
product UI and is not applied here.

## What the research found

**Krause: a feature is an output, a goal is an outcome.** A feature factory
measures "what did we get done" instead of "how valuable is the work we're
delivering". Teams that count shipped features build products that do not
serve the people using them. The unit of work is the person's goal, not the
control that was added.

**Nielsen: every added feature is paid for six times.** Screens get crowded,
so everything on them is harder to find. Documentation grows. People pick the
wrong feature. Feature interactions multiply, with effects nobody predicted.
Decision time rises with the number of options.

**Nielsen: how much richness a product can carry depends on engagement.**
"The more engaged users are, the more features an application can sustain."
Photoshop CS carries hundreds of features because professionals commit to it;
Photoshop Album carried a twenty-page manual because casual users do not.
Website visitors spend about 30 seconds on a homepage and under two minutes on
a whole site, so a website must "focus on the words".

**Perez: context is never neutral.** How information around a decision is
structured, named and retained changes the conclusion drawn from it, and
**more context does not mean better results, because every element competes
for attention**. The four moves are structuring, findability, alignment to
mental models, and deciding what is remembered.

## Placing the audience on the engagement scale

Decide where the users sit on Nielsen's scale. An internal or professional tool
with trained users, a supervisor, and the same screens used dozens of times a
day is at the **engaged** end, not the website end. Such a product **can**
sustain more than a website can, and density is correct for a register. This
file is not an argument for a sparse product, and it is never a reason to
remove something users rely on.

Two things do not transfer, and they set the budget:

- **A worker cannot leave.** A website's cost of complexity is an exit. Here it
  is a wrong approval, an absence not noticed, or a case concluded wrongly. The
  cost is paid by the records, not by the team.
- **The engagement is spent on the work, not on learning the tool.** Where
  there is no tour and no help bubble (Paradox of the Active User), the budget
  buys **depth on the work users already do**, never breadth of options to
  choose between.

## Rules

### 1. Name the goal before naming the feature

Write one sentence:

> **A [role] needs to [goal] so that [outcome], and today they [what they do
> instead].**

- **If the sentence needs the feature's name to make sense, it is a feature,
  not a goal.** "Clerks need an export button" is a feature. "A clerk has to
  give the manager last month's figures and copies them into a notebook" is a
  goal.
- **The goal is the person's**, not the organisation's and not the API's.
- **Say who asked and what happened to them.** A request with no story behind
  it is a guess, and it is worth asking for the story before building.
- **Never settle a business rule here.** Who may do it, how long it lasts,
  what makes it valid: that is the backend's answer. Ask.

### 2. Say how we would know it worked

- **Name the observable change**: the approval queue is empty by the afternoon,
  a complaint is raised once instead of twice, the parallel notebook stops.
- **Not "the feature shipped"**, and not a click count. A feature people click
  because they cannot find the right one is a failure that looks like use.
- **Where there is no analytics**, and the change can only be seen by watching
  a user, say so, and say it has not been watched yet.

### 3. Count the cost before the benefit

Nielsen's six, as they land on a product:

| Cost | In practice |
|---|---|
| **Crowding** | Everything already on the screen gets harder to find. Measure against the screen's one decision (`ui-workflow.md`) |
| **Findability** | One more thing in the navigation, the row or the overflow menu is one more thing to read past |
| **Wrong pick** | Two controls that sound alike is a wrong approval waiting to happen (`voice.md`, one word per thing) |
| **Interactions** | It meets every filter, permission, sort, drill-down and poll already on that screen |
| **Decision time** | Hick's Law. A queue worked dozens of times a day pays this every time |
| **Maintenance** | Four states, a skeleton at the real row shape, its copy, its style-guide entry, and possibly a contract change across repositories |

- **A new feature is also four new states.** Empty, loading, error and
  permission denied are part of the cost, not a later task.
- **Anything on a queue screen is spent from the worker's attention on the
  queue.** That is the scarce thing.

### 4. Try the four cheaper answers first

In order. Go one step down only when the step above genuinely cannot carry it.

1. **It already exists and cannot be found.** Fix the name, the scent or the
   placement (`web-ux.md` §0b). This is the commonest real answer.
2. **The API already returns the value.** Show it in place — a column, a line
   in the sheet, a figure beside the thing it describes. No new destination.
3. **A shared component covers it, extended.** List the components before
   writing one (`ui-workflow.md`). A one-off that looks right on one screen is
   still a net loss.
4. **It is genuinely a new pattern.** Then check reference products first,
   three or more, structure not skin, and write it back into the style guide in
   the same commit.

**Cheapest form that does the job**, in this order: a column, a pill, a chip,
a count, a line in a sheet, a sheet section, a tab, a dialog, a page. Climbing
a step needs a reason said out loud.

### 5. Decide where it lives — the four context questions

Perez's four IA moves, asked about the product:

- **Structure.** Which level does it belong to: the navigation group, the page,
  the card, the row, the sheet, the dialog? Keep navigation to two levels,
  group then page, and a section's pages live in the navigation rather than in
  tabs (`web-ux.md` §3).
- **Findability.** What is it called, and is that the word users already use?
  One word per thing, checked against the existing copy files (`voice.md`,
  rule 11). A name nobody would say out loud is a name nobody will find.
- **Mental model.** Does it fit the nouns users already think in? **A feature
  that needs a new noun needs a very good reason**, because the new noun has to
  be taught, and nothing here teaches.
- **Memory.** What persists, and what must not. The URL holds what is worth
  sharing (the drill-down, the record, the day, the filters). A session holds
  the rest. **Nothing is silently remembered on the person's behalf**: no
  preselected value, and no filter applied without a chip (the `ux-laws` skill, Never
  a deceptive pattern).

### 6. Context is never neutral

What sits beside a figure decides what is concluded from it.

- **A count with no scope is a different fact** from the same count
  with the scope trail above it.
- **Add the context that changes the reading, and nothing else.** More context
  is not better context: every line competes for attention, and a screen of
  true but irrelevant lines is how the important one gets skipped
  (`reading.md`).
- **Every line still passes the five questions** in `voice.md` (What to show).
- **Where the feature could mislead, that is the part to design first**
  (`ui-workflow.md`, Honest screens).

### 7. Show it where the decision is made

- **The place the person already looks**, not a new destination. Selective
  Attention. A queue count belongs on the navigation item, a doubt belongs
  beside the value it doubts, a person's leave history belongs in the leave
  queue.
- **If a new destination is unavoidable**, it gets a visible way in from where
  the person already is (a queue row, a row subject, a labelled link).
- **Deepen, do not lengthen.** Detail goes from the row to a sheet, then a
  tab, then a dialog, never into a longer row or a longer paragraph
  (`reading.md`, rule 4).
- **A queue that somebody waits on goes in the navigation. A number that
  resolves by itself goes in a tile.**

### 8. The forms available, and what each one is for

Cheapest first. Use this to answer "how else could we show it?" without
inventing anything. Map each form to the project's own component.

| What is being shown | Reach for | It earns more when |
|---|---|---|
| A state of one record | A status pill on its row | never — one pill per row is the ceiling |
| A quantity somebody is waiting on | A count badge on the navigation item | it needs a breakdown, then a queue table |
| A quantity that resolves itself | A stat tile | never the navigation |
| A value the API returns | A column, right-aligned in tabular numerals | the shape matters more than the figure, then a chart |
| A doubt about what was typed | A warning panel in the form, saving still allowed | never an error — doubt warns, it does not refuse |
| A refusal | A permission notice, or a dismiss-only dialog saying why | never a disabled control with no reason |
| Supporting detail on a record | A sheet section | it is a list, then a tab |
| A question the app must have answered | A dialog, the question as title | never for a safe action |
| Where the figures came from | The scope trail | — |
| Help that is not needed to act | A help tip | never a standing line, and never the only copy of a reason |
| A choice among many | A dropdown, with search past eight | a multi-select when several apply |

Anything not on this list, and not in the project's style guide, is a new
pattern: check reference products first (`ui-workflow.md`).

### 9. Ideating something new: bring shapes, not a shape

- **Three shapes, then a recommendation.** For each: the form, what it costs
  from rule 3, and what it gives up. One is recommended, in one sentence, and
  the others are named so the decision can be argued rather than guessed at.
- **Every shape is drawn from the vocabulary that exists.** List the shared
  components first. Freshness comes from composition and restraint, never from
  a new colour, size or radius (`self-review.md`, rule 3).
- **Sketch in words at the real content**: a long name in the users' own
  script, a zero, a hundred rows, a value the API does not return yet.
- **Design the four states inside the idea**, not after it.
- **Slice it.** Name the smallest version that ships on its own and is useful
  on its own (`design-specs.md`, rule 5). That slice is usually the whole
  answer.
- **Say what is untested.** Until a real user has used it, the idea is untested
  with users, and the write-up says so.

### 10. Saying no is part of the work

- **A refusal names the goal it does not serve** and offers the nearest thing
  that does, in one or two sentences. Never a lecture.
- **"That is the API's rule" is a real answer**, and the right one for
  anything about who may act, how long a session lasts or what makes a value
  valid.
- **The alternative to a feature is often a subtraction**: a column removed, a
  name fixed, a value shown where the person already looks.

### 11. Review what already ships by the same standard

- **Does it still name a goal?** A feature whose goal nobody can state is a
  candidate for removal.
- **What does it cost the screen around it?** Read rule 3 against the page as
  it is today, not as it was when the feature landed.
- **Would a cheaper form now do?** A page that could be a sheet section, a tab
  that could be a column.
- **Removal needs the same evidence as addition.** Rarely clicked is not
  unused: a worker who needs it once a month needs it. Ask before cutting.
- **A feature that duplicates another under a second name is a defect**, not a
  choice (`voice.md`, rule 11).

## Explaining it so a designer can build from it

The output of this rule is a written answer somebody else acts on. It reads
in this order:

1. **The goal**, in the sentence from rule 1.
2. **What happens today**, in the users' words.
3. **What matters on the screen**: the one decision, what leads, what
   supports, and what is noise.
4. **The recommendation**, in one sentence, with the form named from rule 8.
5. **The options not taken**, one line each, with why they lost.
6. **The cost**, from rule 3, said plainly.
7. **What was not checked**, and what only the business can answer.

Call every element by its name in `style-guide.md` (NN/g's UI glossary and the
project's component), name tokens rather than values, and point at the style
guide's sections instead of restating them.

## Checklist (every feature request or feature review)

- [ ] The goal is one sentence, and it does not need the feature's name
- [ ] Who asked and what happens today are written down
- [ ] How we would know it worked is named, or its absence stated
- [ ] Nielsen's six costs counted against this screen, four states included
- [ ] The four cheaper answers tried first, and the cheapest form chosen
- [ ] Its level, its name, its noun and what persists are all decided
- [ ] It is shown where the decision is made, and it deepens rather than lengthens
- [ ] The context beside it changes the reading, and nothing else was added
- [ ] Three shapes offered with one recommendation, in the system's vocabulary
- [ ] A slice that ships on its own is named
- [ ] New patterns were checked against reference products and written back into the style guide
- [ ] "Untested with users" stated where it applies
