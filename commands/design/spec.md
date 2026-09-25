---
name: spec
description: Write or check the design spec for a screen, feature or component before it is built — flow, tokens, layout, states, real content, accessibility, and the issue side (goal, scope, requirements, use cases, risks) (NN/g, Creating Design Specs for Development)
---

The screen, feature or PR is `$ARGUMENTS`. Read
`.claude/rules/design-specs.md`, `.claude/rules/ui-workflow.md` and
`.claude/rules/style-guide.md` first, then the style guide doc's tokens and
layout sections and the component sections the work touches. Read the existing
page, components and copy files it builds on. Check the back end for the
endpoints and fields it relies on.

**Writing a spec** (nothing is built yet):

1. **Goal**: the one decision the screen serves, and who does it when.
2. **Scope**: in and out, both named.
3. **Requirements**: functional (each business rule names its API answer) and
   nonfunctional (permission, data age, pagination, widths).
4. **Flow**: each click, focus movement, URL state, Back, and confirmations.
5. **Layout**: the supported breakpoints, what repositions or swaps, and what
   scrolls.
6. **Components and states**: shared components by name, and for each the
   empty, loading, error, permission denied, busy and disabled states. Tokens
   by name only.
7. **Content**: the real words, and the long, zero and hundred-row cases.
8. **Accessibility**: tab order, focus on open and close, labels, alt text
   and target sizes.
9. **Risks**: lost input, misleading figures, and contract changes across
   every codebase involved.
10. **References**: style guide sections, and three or more reference links for
    anything the style guide doc does not cover.

Say which parts belong in the style guide doc (reusable) and which in the issue
or PR description (this screen only). If the work is large, split it into slices
that ship on their own. List any question that only the business can answer,
instead of guessing it.

**Checking a spec or PR** (something already exists): walk the
`design-specs.md` checklist. For each gap, report what is missing, why it
matters to the build or the review, and the line to add. Flag any spec that
invents a token, restates a settled component, names a field the API does not
return, or disagrees with the build.

Do not write code as part of this command. If the style guide doc is changed,
run its linter if the project has one.
