# Flow review — finding the gaps between what the person does and what the screens allow

Applies to **any review of a whole flow or of the product's coverage**: "what is
missing?", "where does a task break?", "does this section hang together?". It
is for reading across screens, not for judging one. Sources (NN/g):
[Scenario Mapping: Design Ideation Using Personas](https://www.nngroup.com/articles/scenario-mapping-personas/)
(Kim Flaherty, 2021) ·
[Cognitive Maps, Mind Maps, and Concept Maps](https://www.nngroup.com/articles/cognitive-mind-concept/)
(Sarah Gibbons, 2019).

`ideation.md` finds ideas for one screen. `feature-value.md` decides whether a
thing should exist. `web-ux.md` checks a flow against web conventions. This
file is the sweep that comes before them: **walk each person's real scenarios
across the screens, map the nouns they think in against the nouns the product
has, and list what falls between.**

## What the research found

**Scenario mapping.** A scenario has five parts: the **actor** (a persona), the
**motivator** (what triggered it), the **intention**, the **action**, and the
**resolution**. It is kept high-level, because naming a control ("uses the
filter menu") biases the team toward the solution already built. Broken into
four to six steps, then mined for design ideas, questions and comments. Run the
**same scenario for different personas**, then merge what they share into one
design. Two to four scenarios per session.

**Cognitive, mind and concept maps.** Three ways to draw a mental model:

| Map | Shape | Use here |
|---|---|---|
| **Cognitive** | Free-form, any representation of how a person thinks the thing works | What users believe happens: "if I approve a request, the schedule changes" |
| **Mind** | A tree from one topic, one parent per node | The product's own structure: navigation, pages, tabs, sheets |
| **Concept** | A graph, nodes with several parents and **labelled** links | How the domain's nouns relate (e.g. order, customer, location, staff, schedule) |

They are **not flowcharts**. An enumeration of steps is a scenario, not a map.
Their value is finding **misconceptions and gaps before building**, and
aligning people on the same picture.

## Adapting it to the project

| NN/g | Substitute when research is thin |
|---|---|
| Personas | If there is no persona document or user research, draw the persona from the code, the roles the API returns and the project's style guide, and label it untested with real users |
| Workshop of four to six | A solo reviewer replaces diversity of view by running every scenario as every role, and by reading the backend and any sibling apps for the other side |
| Sticky notes in three colours | Findings in three lists: **gaps** (ideas), **questions** (only the business can answer), **notes** (observations) |
| Concept map of the domain's nouns | Copy or string files, type definitions, the navigation, and `voice.md` rule 11 |
| Mind map of the product | The navigation, routes and the project's style guide |

## Rules

### 1. Write scenarios, not screens

One sentence each, in the five parts, with no control named:

> **[Actor]**, because **[motivator]**, wants to **[intention]**. They
> **[action]** until **[resolution]**.

- **From the person's day**, not the feature list: "A supervisor at the start
  of a shift finds who has not reported and gets them covered."
- **Include the unhappy path**: the wrong person, the missing record, the
  forgotten step, the second attempt, the shared desk.
- **Cover the whole life of the thing**: created, found, changed, acted on,
  concluded, corrected, looked up months later. Most gaps sit at the ends.
- **Two to four per pass.** More and the review goes shallow.
- **Do not settle a business rule.** A scenario that needs one becomes a
  question for the business.

### 2. Break it into four to six steps and walk each screen

For every step, record what the person **needs to see, decide and do**, then
find the screen that gives it. Do this from the code first and the running app
where possible. Mark each step:

- **Served**: a route, a control and a state exist and agree.
- **Partial**: it can be done, but only by leaving, remembering or guessing.
- **Missing**: nothing in the product covers it. Say what is missing, do not
  invent a screen.
- **Blocked by the API**: the value or action does not exist in the backend.

### 3. Look at the seams

Gaps rarely sit inside a screen. Check each seam the step crosses:

| Seam | Question |
|---|---|
| **Entry** | Can the person arrive here from a link, a count in the navigation, a notice, or Back? (`web-ux.md` §0) |
| **Handoff** | When the step ends, does the next screen know what was just done? Does the record show who did it and when? |
| **Return** | After acting, does the person land on the row they left, with filters kept? |
| **Other role** | When this role finishes, does the next role see it? Who is told, and where? |
| **Other app** | Is the same record visible in any other client or the backend under the same word and state? |
| **Failure** | What does the person see when it fails partway, and can they resume without redoing it? |
| **Dead end** | Any screen with no way forward and no way back other than the navigation |
| **Orphan** | A page, tab or action no scenario reaches |

### 4. Run it as every persona, then merge

- **The same scenario for each role that touches it.** The person who raises a
  record, the one who resolves it and the one who audits it see three different
  flows of one record.
- **Look for what is shared** and check the record reads the same on every
  role's screen.
- **A permission gap is a scenario**: a role that is meant to do a task but
  cannot reach it, or reaches it and sees nothing (`web-ux.md` §2).

### 5. Draw the concept map of the nouns

Once, per area, and again when a feature adds a noun.

1. **List the nouns** users say (`voice.md`, "Words to use").
2. **Draw the labelled links** between them: "a *location* belongs to a
   *region*", "a *complaint* is raised against a *location*", "*leave* changes
   a *schedule*". Labels are verbs.
3. **Compare with the product.** For each noun and each link ask:
   - Is there a place to **see** it, **change** it and **find** it?
   - Is the link **navigable** in both directions, or one way only?
   - Does the screen call it by the users' word (`voice.md` rule 11)?
   - Is there a noun on screen that users do not use, or a code word
     (`recognition-over-recall.md` rule 4)?
4. **A link that exists in the domain and not on screen is a gap.** A noun the
   product invented is a finding. A link users believe that the system does not
   honour is a **misconception**, and the most costly kind.

This is a concept map, not a flowchart. Do not list steps in it.

### 6. Sort the findings into three lists

- **Gaps**: something the person needs that is missing or partial. Each names
  the scenario and step, the seam, and the cheapest form that would close it
  (`feature-value.md` rule 4 and 8). A gap is not yet a feature. It goes through
  `feature-value.md` before any screen is designed.
- **Questions**: what only the business or the backend can answer. Never
  guessed.
- **Notes**: things observed that are fine, or already decided. Say what was
  found working, so a review is not only a list of faults.

Rank gaps by **cost to the record**: a wrong or missed action outranks a slow
one, and a slow one outranks an untidy one (the `ux-laws` skill, Pareto).

### 7. Say what was not seen

- **Untested with users.** If personas and scenarios come from the code, not
  from the people who use it, state it.
- **From the code, or from the running app.** Say which, per scenario.
- **Which of the backend and sibling apps were checked**, and which were not.

## Checklist (every flow review)

- [ ] Two to four scenarios, each in the five parts, with no control named
- [ ] Each scenario covers the unhappy path and the whole life of the record
- [ ] Every step marked served, partial, missing or blocked by the API
- [ ] Seams checked: entry, handoff, return, other role, other app, failure, dead end, orphan
- [ ] The scenario run as each role that touches it, and the shared record reads the same
- [ ] A concept map of the nouns compared with the screens, misconceptions named
- [ ] Findings in three lists (gaps, questions, notes), ranked by cost to the record
- [ ] Gaps routed to `feature-value.md`, not built
- [ ] "Untested with users" and what was checked from where stated
