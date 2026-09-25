# Design specs — what gets written down before a screen is built

Applies to **every new screen, feature or shared component**, and to any change
large enough that someone else (a reviewer, the back-end side, a later session)
needs to know what was meant. Source:
[Creating Design Specs for Development](https://www.nngroup.com/articles/creating-design-specs-for-development/)
(Kelley Gordon, NN/g, 2025).

NN/g defines a design spec as the material that gives "all relevant information
on the functionality, behavior, and appearance of a design" so design and
development stay aligned. It has two parts: **the design file**, and **the
development issue**, which acts as a contract between the two.

`style-guide.md` decides what the style guide doc must hold for a shared
component. `self-review.md` decides how finished work is handed over. This file
decides **what is written before the build**, and where.

## Where a spec lives

Where there is no design tool file, split the spec by how long it must live:

| NN/g part | Here |
|---|---|
| Design file: reusable patterns | The style guide doc (e.g. `DESIGN.md`), the entry `style-guide.md` defines |
| Design file: one screen | The issue or PR description, pointing at the style guide entries it uses |
| Development issue | The same issue or PR description |
| The API side | The back-end repo or docs: the endpoints, fields and errors the screen relies on |
| Screenshots | Attached to the PR, taken from the running app |

**A pattern two screens could use goes into the style guide doc**, not only
into a PR that will be closed and forgotten.

## Rules

### 1. The design side says what it does, looks like and says

For each screen, the spec covers NN/g's six areas:

- **Interaction flow.** What each click does, where focus goes, what the URL
  holds, what Back does, and which actions confirm (`interactions.md`).
- **Visual design.** Token names only (e.g. `accent`, `ink-muted`). Never a hex
  code or a size the tokens do not have. A spec that needs a new value changes
  the style guide doc first.
- **Layout.** Behaviour at the supported breakpoints, what repositions or
  swaps, and which region scrolls.
- **Components and their states.** Which shared components, by name
  (`ui-workflow.md`, List the components). For each: empty, loading, error,
  permission denied, busy and disabled, and any motion by token
  (`motion.md`).
- **Real content.** The actual words from the copy file or the proposed ones
  (`voice.md`). Real lengths: a long name, a zero, a hundred rows, a name in
  another script. No lorem ipsum and no "Label".
- **Accessibility.** Tab order, where focus moves on open and close, labels
  for icon-only controls, alt text for photos, and target sizes
  (`target-size.md`).

### 2. The issue side says why, how far, and what could go wrong

NN/g's development issue, as the PR or issue description:

- **Goal**: the one decision the screen serves (`ui-workflow.md`).
- **Scope**: what is in, and **what is out**, named. Silent scope reduction is
  not allowed.
- **Functional requirements**: what the person can do. Each business rule
  names the API answer it comes from, never a rule the client invents.
- **Nonfunctional requirements**: permissions, data age and refresh,
  pagination, performance, and the browsers and widths it must work at.
- **Use cases**: who does it and when, in the users' own words ("A
  supervisor allows leave at the start of a shift").
- **Risks and mitigations**: lost input, a misleading count, a contract change
  in another codebase, a migration of existing data.
- **References**: the style guide sections, the reference links (three or more
  products), and the screenshots.

### 3. Talk to the other side early

- **Check the back end before assuming a shape.** A spec that names a field the
  API does not return is not a spec.
- **A contract change is a change in every codebase that uses it.** The spec
  says which of them move.
- **Name what can be traded.** Mark the essentials, and say which details can
  give way if the build is costly.
- **Ask when a requirement is ambiguous.** Do not settle a business rule in
  the spec.

### 4. Keep it true

- **The spec changes when the design does**, in the same commit or PR update.
- **Screenshots match the build.** An outdated screenshot is a wrong spec.
- **Where the build and the spec disagree**, one of them is corrected and the
  difference is recorded (`style-guide.md`, rule 4).

### 5. Keep it small

- **Split a large spec into slices** that ship on their own: one table, one
  side sheet, one dialog. Each slice is one PR.
- **Point, do not copy.** A spec links to the style guide doc and the component
  file. It never restates tokens or a settled component.

### 6. It comes before the code

The order is the one in `ui-workflow.md`: read the style guide doc, find the
reference, **write the spec**, then build. A spec written after the build only
describes what happened.

## Checklist (every new screen or feature)

- [ ] Flow, visual tokens, layout, component states, real content and accessibility are all covered
- [ ] Goal, scope in and out, functional and nonfunctional requirements, use cases and risks are written
- [ ] Every business rule names its API answer, and the back end was checked
- [ ] Reusable patterns went into the style guide doc, and the rest into the issue or PR
- [ ] Tokens and components are named, never copied or invented
- [ ] Screenshots are from the running app and match the build
- [ ] Large work is split into slices that ship on their own
- [ ] The spec was written before the code
