# Style guide — keeping the style guide doc a living front-end style guide

Applies to **every change that adds, changes or removes a shared component,
token or pattern**, and to any edit of the project's style guide doc (e.g.
`DESIGN.md`). Sources (NN/g):
[Front-End Style Guides: Definition, Requirements, Component Checklist](https://www.nngroup.com/articles/front-end-style-guides/) ·
[User-Interface Elements: Glossary](https://www.nngroup.com/articles/ui-elements-glossary/).

NN/g defines a front-end style guide as "a modular collection of all the
elements in your product's user interface, together with code snippets for
developers to copy and paste". The guide is **living**: it changes with the
product, or the product drifts from it. The guide is the style guide doc
together with the component folder and the token config. Its two benefits are
the reasons to keep it current: **efficiency** (a screen can be specified as
"which components go where") and **consistency** ("if it's less work to do the
right thing", people do it).

It is not an editorial guide (that is `voice.md`), and it is not only a brand
guide (colour, type). It covers both, plus the components.

## What the guide must contain (NN/g's eight requirements)

| # | NN/g requirement | Where it lives |
|---|---|---|
| 1 | A table of contents in findable categories | The doc's headings, with components ordered so they can be found |
| 2 | The layout grid and responsive rules | The doc's layout, spacing and breakpoints section |
| 3 | The colour palette in the platform's format | The doc's colour section, and the token config |
| 4 | Type: family, sizes, weights, line height, usage | The doc's type section, and the token config |
| 5 | For each element, **when to use it** | The component's entry in the doc |
| 6 | For each element, **the code** | The component's path in the source tree, named in its entry |
| 7 | For each element, **spacing and specs** | The same entry: height, padding, radius, tokens |
| 8 | For each element, **dos and don'ts** | The same entry, with the decision and what was rejected |

**A component is not finished until its entry has all four of 5–8**, plus its
states (empty, loading, error, permission denied) and its reference links.

## Use NN/g's names

Call an element by its name in the
[UI elements glossary](https://www.nngroup.com/articles/ui-elements-glossary/),
so a spec, a reference search and a review use the same words. Map each glossary
term the product has to its component, for example:

| NN/g term | Map to the project's component |
|---|---|
| Button, split button | Button |
| Link | Inline and row links |
| Textbox | Text field, textarea |
| Dropdown list / listbox | Dropdown, select |
| Listbox (multi-select) with tokens/chips | Multi-select |
| Checkbox | Checkbox or multi-select rows |
| Date picker | The date input |
| Tabs | Tabs |
| Navigation menu, submenu (flyout) | Side or top navigation |
| Side sheet (drawer, flyout) | Sheet |
| Dialog (modal) | Dialog |
| Lightbox | Photo viewer |
| Card, container | Card, stat tile |
| Badge | Nav and tab counts |
| Tooltip | Tooltip or help tip |
| Skeleton screen, spinner | Skeleton, spinner, button loading state |
| Scrollbar | Scrollbar styles |
| Breadcrumbs | Scope or path trail |
| Icon | The shared icon set |

**List what the product does not have, and do not add it without a decision in
the guide.** Candidates from NN/g's glossary: carousel, floating action button,
snackbar or toast, slider, knob, toggle switch, stepper, accordion, megamenu,
pie menu, contextual (right-click) menu, bottom sheet, back-to-top button.
NN/g: "use only components present in your product", so the guide never lists
what the product does not have.

## Rules

1. **Code and guide change together.** A new shared component, a new variant or
   a changed spec updates its entry in the same commit.
2. **The guide names the file.** Every entry for a built component names its
   path, so "the code snippet" is one click away.
3. **The guide never keeps a second copy of a token file.** It points at the
   token config. A copy drifts.
4. **Specs describe what ships.** Where the guide and the code disagree,
   `ui-workflow.md` decides which moves. The gap is never left unrecorded.
5. **Record the rejected option.** A do-and-don't without the don't is how the
   next screen reopens the decision.
6. **Shared brand values stay shared.** A brand value used by more than one
   codebase changes in all of them.
7. **One name per thing** in the guide, the code and the UI copy.

## Checklist (any component or token change)

- [ ] The entry exists and has: when to use, the code path, specs, dos and don'ts, states, and reference links
- [ ] The element is called by its NN/g glossary name
- [ ] Nothing listed that the product does not have
- [ ] No token values copied into the guide beyond the single place designated for them
- [ ] Code and guide agree, or the disagreement is recorded
- [ ] A shared brand value changed in every codebase that uses it
