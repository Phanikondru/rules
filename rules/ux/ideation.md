# Ideation — how a good idea is found before it is judged

Applies to **any moment where the question is "what could this be?"**: a new
feature, an improvement to a screen that ships, a page that feels flat, or a
teammate's idea worth learning from. It runs **before** `feature-value.md`
decides whether an idea earns its place, and before `design-specs.md` writes it
down. Sources (NN/g):
[Ideation for Everyday Design Challenges](https://www.nngroup.com/articles/ux-ideation/) ·
[Ideation in Practice](https://www.nngroup.com/articles/ideation-in-practice/) ·
[Using "How Might We" Questions](https://www.nngroup.com/articles/how-might-we-questions/) ·
[Functional Fixedness Stops You From Having Innovative Ideas](https://www.nngroup.com/articles/functional-fixedness/) ·
[Beating Creative Blocks Through Reframing](https://www.nngroup.com/videos/beating-creative-blocks-reframing/) ·
[Personas vs. Jobs-to-Be-Done](https://www.nngroup.com/articles/personas-jobs-be-done/) ·
[Journey Mapping 101](https://www.nngroup.com/articles/journey-mapping-101/) ·
[Troubleshooting Group Ideation](https://www.nngroup.com/articles/group-ideation/) ·
[Parallel & Iterative Design + Competitive Testing](https://www.nngroup.com/articles/parallel-and-iterative-design/) ·
[UX Mindsets: Fixed Versus Growth](https://www.nngroup.com/articles/mindsets-fixed-vs-growth/) ·
[Dashboards: Making Charts and Graphs Easier to Understand](https://www.nngroup.com/articles/dashboards-preattentive/).

`feature-value.md` asks whether a thing should exist and which form is
cheapest. This file is the step before it: **how to produce the shapes worth
judging**, and the habits of thought that make a designer find an idea such as
playing a trail back through time instead of only drawing it.

## What the research found

- **Ideation is generating a broad set of ideas with no attempt to judge them.**
  Evaluation stifles creativity, so diverging and converging are separate
  phases. Quantity first, judgment later, unusual ideas welcome, build on
  others.
- **The first idea is rarely the best.** Parallel design of three to five
  alternatives, merged, measured 70% better than the single best design and
  56% better than the originals, and one further iteration reached 152%. The
  gain comes from exploring the range before refining one path.
- **Order matters.** 71% of teams with a very effective process ideated after
  user research and before prototyping, against 48% of the rest.
- **Structure and writing beat open talk.** 95% of the least effective teams
  used only unstructured discussion. Teams rating themselves very effective
  used written techniques twice as often, and had fewer people ideating alone.
- **Research is the strongest source.** 74% of very effective teams drew on
  user research, against 45% of ineffective ones. Competitors (78%) and
  colleagues (76%) came next.
- **Functional fixedness is the blocker.** Experience makes people see an
  object, or a screen, only in the way it is already used. The cure is to
  **abstract the problem**: strip the surface details, restate the core
  problem, look in a distant field that has solved the same structure, then
  bring the idea home. A break between steps helps.
- **A How Might We question frames the problem without prescribing the fix.**
  It comes from a real finding, states a desired outcome in positive words, is
  broad enough to leave room, and contains no solution.
- **Jobs to be done ask why, not how.** People want the hole, not the drill.
  Accepting today's workflow as fixed is how a team optimises the wrong thing.
- **A journey map shows where the experience breaks and where it delights.**
  Opportunities sit at the moments of friction and the moments where the person
  is guessing.
- **Do not copy a competitor.** A design that looks good may not be usable.
  Take the idea, then test it.
- **Mindset is behaviour.** A growth mindset tries an approach before dismissing
  it, treats a critique as material, and balances research with action. A fixed
  one says "we have always done it this way" and uses research as a bottleneck.
- **A dashboard's overview is read at a glance** and carries minimal
  interaction. Exploration belongs to the place a person goes on purpose.

## Fitting it to the project's process

| NN/g | In practice |
|---|---|
| Ideate after research, before prototyping | Goal, style guide, reference products, spec, build (`ui-workflow.md`) |
| Parallel design, three or more | `feature-value.md` rule 9: three shapes and a recommendation |
| Written, structured technique | `/ideate` writes the lenses and the ideas down |
| Competitive inspiration | Three or more reference products, structure not skin (`ui-workflow.md`) |
| Research as the source | If there is no analytics or user sessions, the code, the API and users' workarounds stand in, and the result is labelled untested with users |
| Overview at a glance, exploration on purpose | Overview tiles stay still. Exploratory views are pages the person opens |

## Rules

### 1. Start from what the person is trying to understand

Not from a control and not from a chart type. Write the person's question in
their words ("Did he really stay at the site, and when?"), then ask what the
current screen makes them do to answer it (`feature-value.md` rule 1). Every
workaround is a signal: hovering point by point, copying times into a notebook,
opening a second tab.

### 2. Find what the screen flattened

Data is often stored as a story and shown as a still. For any screen that
shows a result, ask which of these was lost on the way. This is a house lens,
drawn from the journey-map and jobs-to-be-done reading above, and it is where a
static trail becomes a playback:

| Lost | Question | The shape it takes |
|---|---|---|
| **Time** | In what order, and how long? | A timeline, a scrubber, playback, a per-day strip |
| **Direction** | Which way, from where to where? | Arrows, a start and an end, an ordered list |
| **Change** | Better or worse than before? | Against yesterday, last week, the person's own usual |
| **Comparison** | Compared with whom or what? | Two days, two people, the roster, the target |
| **Cause** | What happened just before? | The event beside the value, a record's history |
| **Absence** | What is missing that should be here? | A roster built from who was meant to be there (`web-ux.md` §4) |
| **Uncertainty** | How sure is this? | The doubt beside the value, marked as estimated |
| **Next step** | What does the person do about it? | The action on the row, not a new page |

A lens that finds nothing is reported as finding nothing. Do not invent a gap.

### 3. Abstract before proposing

When the first idea is the one the screen already suggests, that is functional
fixedness. Restate the problem with the surface removed, then look elsewhere:

1. **Strip the nouns.** "Show the path a person took" becomes "Show how a thing
   moved through space and time".
2. **Name a distant field that solved the same structure**: a flight tracker,
   a video timeline, a sports replay, a clinical chart, a court record, a
   train's arrival board.
3. **Bring back the mechanism**, not the skin. It still has to be built from
   the project's existing patterns and pass its motion rules.

Take a break between steps, and never abstract into a field the users would
find odd.

### 4. Write How Might We questions, not solutions

Three to five, from a real finding, each passing NN/g's check:

- Based on an actual problem the code, the API or a workaround shows.
- Tracks a desired outcome, in positive words.
- Broad enough to leave room, narrow enough to stay on the problem.
- **Contains no solution.** "How might we show the trail as a video" fails.
  "How might a supervisor see the order and pace of a person's day at a glance"
  passes.
- Not generic. "How might we improve the map" fails.

### 5. Diverge on paper: quantity, no judging

- **At least eight rough ideas** before any is ruled out, including a bad one
  and a boring one. Write them as a line each.
- **Judge nothing in this step.** "The rules do not allow it" is a step-7
  question, not a step-5 one.
- **Include the subtraction**: one idea is always to remove something, or to
  leave the screen as it is (`feature-value.md` rule 10).
- **Include the cheapest**: a cue, a column or a line in a sheet before a
  page.
- **Set the first idea aside.** It is often the one already in the code.

### 6. Converge into three shapes

Cluster the ideas, then carry three into `feature-value.md` rule 9: the form,
where it lives, what it costs, what it gives up, and one recommendation. Take
the cheapest that answers the person's question and name the slice that ships
alone. Iterate the chosen one after it has been seen, not before.

### 7. Check the constraints as the second pass, never the first

A good idea is judged against the system **after** it has been imagined, so the
system shapes the idea rather than preventing it. In this order:

1. **Honesty** (`ui-workflow.md`, Honest screens): does it show what it does not
   know? Interpolated positions, missing fixes and faked values are marked.
2. **The API**: does the data exist, and who owns the rule?
3. **The style guide and the rules**: motion (`motion.md`), scroll
   (`scroll-fading.md`), keyboard (`interactions.md`), target size, voice. If
   the idea needs a new pattern, check reference products and record it in the
   style guide first.
4. **Reading and density** (`reading.md`, `dense-pages.md`): does it add or
   replace?
5. **Where it lives** (`feature-value.md` rule 5). Overview tiles are read at a
   glance and stay still. Exploration lives on a page the person opens.

An idea that fails a constraint is reshaped or sliced, not dropped. A playback
that cannot animate under `motion.md` becomes step-through.

### 8. Borrow the idea, test the fit

- **Look at three or more products** for anything new (`ui-workflow.md`).
- **Take the structure and re-clothe it** in the project's tokens. Do not copy a
  look, and do not copy an interaction whose cost is unknown.
- **Learn from a teammate's solution the same way.** Name the problem it
  solved, the lens it used and the cost it carries, before deciding whether it
  ships. A good idea from a colleague still goes through rules 6 and 7.

### 9. The mindset, as behaviours

- **Ask why the screen is the way it is** before asking how to improve it.
- **Try before dismissing.** Sketch the idea in words at the real content
  before saying it will not work.
- **Say the assumption**: "this assumes users want to watch, not just read".
- **Hold ideas lightly and evidence firmly.** An idea is a hypothesis until a
  real user has used it, and until then it is labelled untested.
- **Never let research become a bottleneck.** Take what the code, the API and
  the workarounds show, act on it in the smallest slice, and learn.
- **Take a critique as material**, including one from the rules.

### 10. Do not confuse novelty with value

An idea is not better because it is impressive. It is better because it makes
the person's one decision faster, safer or more certain. If it cannot say how
it would be known to have worked (`feature-value.md` rule 2), it is a demo.
Motion and imagery that carry no information stay out (`motion.md`,
`visual-design.md`).

## Worked example: a person's day on a map

- **Person's question**: "Where was this person, in what order, and for how
  long?"
- **What it costs today**: hover point by point, read the timeline rows against
  the line.
- **Lens**: time and direction were flattened. The line has no order and no
  direction.
- **Abstraction**: "how a thing moved through space and time" points to a
  replay, a video timeline and a flight tracker.
- **HMW**: How might a supervisor see the order and pace of a person's day at
  a glance?
- **Ideas**: arrows on the line, a Start and End label, a scrubber, a stepper
  through fixes, playback with speed steps, a per-hour strip, a comparison with
  yesterday, colour by time of day, a list only, and "leave it".
- **Three shapes**: arrows only, arrows plus step-through, full playback.
- **Constraints**: playback needs a motion decision, an honest marker across
  "No signal" gaps, faked positions handled, reduced motion, and a keyboard
  equivalent.
- **Slice**: arrows first, since they answer direction and add no motion.

## Checklist (every ideation)

- [ ] The person's question is written in their words, with today's workaround
- [ ] The lenses were run and what was flattened is named, or "nothing found" said
- [ ] The problem was abstracted and one distant field consulted
- [ ] Three to five How Might We questions, none containing a solution
- [ ] At least eight ideas written before any was judged, including a subtraction and a cheap one
- [ ] The first idea was set aside and revisited
- [ ] Three shapes carried into `feature-value.md`, with one recommendation and a slice
- [ ] Constraints checked after the idea, in order, and a failing idea reshaped
- [ ] Three or more products looked at for anything new, structure taken and not skin
- [ ] "Untested with users" stated
