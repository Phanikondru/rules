---
name: web
description: Review a web app flow for web UX — access and permission gating, navigation and URL, the four table tasks and filters, input fields, breakpoints and screen space, shared desks (NN/g)
---

The flow or page is `$ARGUMENTS`. Read `.claude/rules/web-ux.md` first. Then
read the route definition, the page, its guards and permission helpers, the
navigation entry, and the components it uses.

Check, in order:

1. **Onboarding**: no tour, coach mark or promotion. Help appears where the
   person gets stuck.
2. **Access**:
   - gated by permission
   - a person never lands on an empty page
   - a 403 is a permission notice in plain English
   - no business rule in the client
3. **Navigation**:
   - navigation, then page, then tabs only inside a record
   - shareable state in the URL, and Back undoes the last step
   - links open in a new tab
   - queue counts on the navigation
4. **Tables**: find (filters as chips, sort), compare (right-aligned tabular
   numerals, no repeated column), view (subject link, sheet) and act
   (row actions, destructive confirmed). The headcount comes from the server.
5. **Fields**: run the input checklist in `web-ux.md` on each field, starting
   with "is it needed at all?"
6. **Space**: one breakpoint system for new work, two panes only at wide
   breakpoints, and wide tables scroll inside their card.
7. **Shared desks**: the signed-in person is visible, and nothing sensitive is
   logged or put in the URL.
8. **Text load**: pass the page through `.claude/rules/reading.md`.

Report findings with the rule and its source, and the fix. Mark anything that
needs an API decision (roles, session length, password rules, what a field
exposes) as a question for the backend, not a client change.
