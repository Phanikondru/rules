---
name: flow
description: Review a flow or a whole area for gaps — write persona scenarios, walk each step across the screens, check the seams between them, and map the domain's nouns against the product (NN/g: scenario mapping, cognitive, mind and concept maps)
---

The flow, area or role is `$ARGUMENTS`. If it is empty, review the whole
product, one section of the navigation at a time. Read
`.claude/rules/flow-review.md` first, then the project's style guide for what
exists, `.claude/rules/web-ux.md` for the navigation rules, and
`.claude/rules/feature-value.md` for what happens to a gap. Then read the
routes, the navigation, the pages, the copy files and the type definitions for
the area. Check the backend and any sibling apps for the other side of any
record the flow touches, and say if they were not available.

1. **Personas.** Name the roles that touch the area, from the code and the
   roles the API returns. Say plainly they are untested with real users.
2. **Scenarios.** Write two to four, each as actor, motivator, intention,
   action and resolution, with no control named. Include an unhappy path and
   the whole life of the record, from raised to looked up months later.
3. **Walk each scenario** in four to six steps. For each step, name what the
   person needs to see, decide and do, and mark it served, partial, missing or
   blocked by the API.
4. **Seams.** For every step check entry, handoff, return, other role, other
   app, failure, dead end and orphan.
5. **Every role.** Run each scenario as each role that touches it and check
   the shared record reads the same.
6. **Concept map.** List the domain's nouns, draw the labelled links between
   them, and compare with the product. Name every link that exists in the
   domain and not on screen, every invented noun, and every misconception.
7. **Sort** into three lists: gaps, questions for the business, and notes on
   what works. Rank gaps by cost to the record.

If the app can be run (`/run`, or the Chrome tools), walk the main scenario
in it and say which steps were confirmed there and which were read from code.

Report the scenarios first, then a table of steps and their marks, then the
three lists. Each gap gives the scenario and step, the seam, the source
(`file:line` or the missing route), and the cheapest form that would close it.
Do not write code or design a screen. Route each gap through `/feature`, and
say that nothing here has been tried with real users.
