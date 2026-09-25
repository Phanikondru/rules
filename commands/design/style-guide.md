---
name: style-guide
description: Check the style guide doc is a complete, living front-end style guide — every shared component documented with when to use, code path, specs, dos and don'ts, states and reference links, named by NN/g's UI glossary, with no drift from the code (NN/g front-end style guides)
---

Check the style guide for `$ARGUMENTS`: one component, a group of components,
or everything if nothing is named. Read `.claude/rules/style-guide.md` first.

1. **Inventory the code**: list the shared components in the project's
   component folder, and the tokens in the token config and global styles.
2. **Inventory the guide**: list the style guide doc's headings, component
   entries and token tables.
3. **Match them**:
   - a component with no entry
   - an entry for something that is not built, not marked as planned
   - an entry that does not name its file
4. **Check each entry** for NN/g's four per-element requirements (when to use,
   the code, specs, dos and don'ts), plus its states and its reference links.
5. **Check agreement**: for each spec value (height, padding, radius, colour
   token, duration), compare the guide with the component's code. List
   every disagreement with both values and `file:line`.
6. **Check names**: each element's name against NN/g's glossary, and the same
   name in the guide, the code and the UI copy.
7. **Check brand sync**: if brand values are shared with another codebase,
   compare them and list anything not recorded as an intentional difference.

Report as a table: element, what is missing or wrong, and the fix. Do not
change code or the guide unless asked. When asked to fix, update the guide to
describe what ships, or flag where the code should move instead, following
`ui-workflow.md`.
