# Web UX — navigation, access, tables, filters, fields and shared desks

Applies to **navigation structure, sign-in and access, permission gating,
tables, filters, input fields, screen space and breakpoints** in a web app.
Sources are linked under each section.

Related rules: overlays and keyboard are in `interactions.md`, how much text a
screen carries is in `reading.md`, motion is in `motion.md`, and the look is in
`visual-design.md`. The wider reading list is NN/g's
[Web UX Study Guide](https://www.nngroup.com/articles/web-ux-study-guide/).

## 0. A web app, not a desktop program

[The Difference Between Web Design and GUI Design](https://www.nngroup.com/articles/the-difference-between-web-design-and-gui-design/)
(Nielsen) ·
[URL as UI](https://www.nngroup.com/articles/url-as-ui/) (Nielsen)

Nielsen's point is that a web designer must "give up full control". A web app
follows the web's rules:

- **The person controls the view.** Browser zoom, window size, and the
  system's font and motion settings are respected, and the layout adapts rather
  than fighting them.
- **The person controls navigation.** Any page can be the first page: from a
  bookmark, a pasted link, a reload or a new tab. Every page stands alone, with
  its title, its scope and a way back into the navigation. No flow depends on
  having arrived from a particular page, except a forced first-run step such as
  a mandatory password change.
- **Web conventions win over novelty.** People bring the web's habits: a Ctrl
  or Cmd click opens a new tab, Back goes back, and the logo at the top left
  goes home (it links to `/`). "The Web as a whole has become a genre" (Nielsen).
- **The URL is interface.** Paths are short, lowercase, hyphenated, readable,
  and describe the structure (`/attendance/away`, `/settings?view=cameras`).
  **A shortened path should reach its parent**: `/attendance` should redirect to
  the section's first page, not fall through to a 404. **URLs are permanent**: a
  renamed route keeps a redirect from the old one, because links to it live in
  chats and bookmarks. Query parameters use readable names
  (`?cluster=&post=&date=`).

## 0b. Information scent and links

[Information Scent](https://www.nngroup.com/articles/information-scent/) ·
[A Link Is a Promise](https://www.nngroup.com/articles/link-promise/) ·
[Guidelines for Visualizing Links](https://www.nngroup.com/articles/guidelines-for-visualizing-links/) ·
[Opening Links in New Windows](https://www.nngroup.com/articles/new-browser-windows-and-tabs/) ·
[The 3-Click Rule Is False](https://www.nngroup.com/articles/3-click-rule/)

- **Every label predicts what is behind it.** Navigation items, queue rows and
  links use the destination's own title. People follow scent, not click counts.
  A fourth click with strong scent beats a second one with none.
- **Links look like links**: underlined, in the link or accent colour. Nothing
  else is underlined.
- **Links open in the same tab by default.** The person chooses a new tab. The
  exceptions, which say so, are a file download and a page outside the app.
- **Scope is shown where it applies.** A scope trail acts as breadcrumbs
  ([Breadcrumbs](https://www.nngroup.com/articles/breadcrumbs/)): the current
  level is plain text, earlier levels are links, and it never replaces the main
  navigation.

## 1. No onboarding; the screen teaches

[Paradox of the Active User](https://lawsofux.com/paradox-of-the-active-user/)

- **No tour, no coach marks, no help bubble** where users are trained or
  supported by someone else (check the project's style guide).
- **Teach at the moment of need**: a hint under a field, a warning panel beside
  a doubtful value, an empty state that says what fills it.
- **Never promote a feature.** A new feature is announced once at most, where
  it is used.
- **No trial or upgrade furniture** in an internal tool.

## 2. Access: the API decides, the screen explains

- **Sign-in, session length, lockout and password rules are the API's.** The
  screen shows its answer in plain words.
- **A route guard forces a mandatory step** (such as a password change) while
  the flag is set. Never route around it.
- **Gate by permission** with the project's permission helper, route guard and
  navigation gating. A person never lands on a page that shows them nothing.
- **A refusal says what the person would need**, in plain English. Never a
  permission key, and never an empty table.
- **A section the person may not see is not drawn**, not drawn empty.

## 3. Navigation: shallow, labelled, visible

[Menu Design Checklist](https://www.nngroup.com/articles/menu-design/) ·
[Hamburger Menus](https://www.nngroup.com/articles/hamburger-menus/)

- **Side navigation is the navigation** on a desktop app: groups with labelled
  pages, and the current page clearly marked. No hamburger at desktop widths.
- **Two levels only**: group, then page. A section's pages live in the
  navigation, so a page does not also carry tabs for them. Tabs are for lists
  inside one record.
- **Queue counts sit on the navigation item**, and survive a collapsed
  navigation.
- **The URL holds the state worth sharing**: the drill-down, the chosen record,
  the day and the filters. Back undoes the last step, and a link can be sent.
- **Links are links**: middle-click and "open in new tab" work on anything that
  navigates.
- **A destination that matters has a visible way in** from where the person
  already is (queue rows, "View on map").

## 4. Tables and filters: the four table tasks

[Data Tables: Four Major User Tasks](https://www.nngroup.com/articles/data-tables/) ·
[Applying Filters](https://www.nngroup.com/articles/applying-filters/)

NN/g's tasks are: find records, compare, view or edit one, and act on it.

- **Find**: search and filters above the table, with every applied value as a
  removable chip. Sort from the header.
- **Compare**: numbers right-aligned in tabular numerals, a header that carries
  the word so the cell carries the figure, and no column that repeats one value.
- **View one**: the subject is the underlined link. A record opens in a side
  sheet over its list, or on its own page when it is large.
- **Act**: row actions on the row or in its overflow menu, with the
  destructive one confirmed.
- **Filters apply at once** for single choices. Say how many rows match.
- **A roster table is built from who was meant to be there**, never from the
  records that came in.
- **A headcount is the server's.**
- **Pages, not infinite scroll**
  ([Infinite Scrolling](https://www.nngroup.com/articles/infinite-scrolling/)).
  A register is goal-driven work, where the person needs to know where they are
  and how many are left. The pager states it.
- **Keep the person's place**
  ([Saving Scroll Position](https://www.nngroup.com/articles/saving-scroll-position/)).
  Closing a sheet or going Back returns to the same row. Filters, sort and page
  survive a return.
- **No horizontal scrolling of the page**, and none that mimics swipe on
  desktop
  ([Horizontal Scrolling](https://www.nngroup.com/articles/horizontal-scrolling/)).
  A wide table scrolls inside its card, with the cut-off column visible.
- **Filters, not facets, unless the API returns counts**
  ([Filters vs. Facets](https://www.nngroup.com/articles/filters-vs-facets/)).
  Never show a value that leads to zero results as if it had some.
- **A search with no results** says what was searched, that nothing matched,
  and offers to clear the filters
  ([No-Results Pages](https://www.nngroup.com/articles/search-no-results-serp/)).
- **No carousel**, and nothing that advances on its own
  ([Carousel Usability](https://www.nngroup.com/articles/designing-effective-carousels/) ·
  [Auto-Forwarding](https://www.nngroup.com/articles/auto-forwarding/)). If a
  set of photos ever gets next and previous in a viewer: five or fewer is
  best, show "2 of 5", put the controls inside the frame, make them large and
  labelled (not dots), and never auto-advance.
- **No accordion hiding what the task needs**
  ([Accordions on Desktop](https://www.nngroup.com/articles/accordions-on-desktop/)).
  On a desktop, show the content. Tabs are for parallel lists read one at a
  time ([Tabs, Used Right](https://www.nngroup.com/articles/tabs-used-right/)).

## 5. Input fields: fewer, filled in, forgiving

[Website Forms Usability: Top 10 Recommendations](https://www.nngroup.com/articles/web-form-design/)

Before adding a field, check each point:

1. **Is it needed at all?** The API decides what is required.
2. **Label above, placeholder as example only.**
3. **Required or optional is visible before saving.**
4. **One column** unless the fields are a pair.
5. **The box fits a typical answer.**
6. **Fill it in where the system knows the answer**, and say so.
7. **The right input type and autocomplete**, and paste works.
8. **Accept many formats and normalise them silently**: spaces, country codes,
   a leading 0.
9. **Errors inline, specific, and kept until fixed** (`forms-and-selection.md`).

Sign-in specifically:

- **The password field reveals itself.**
- **The browser's password manager works**: correct `autocomplete`, `name` and
  a real `<form>`.
- **Where the person cannot recover access themselves, say who to call.**

## 6. Use the screen for the work

[Utilize Available Screen Space](https://www.nngroup.com/articles/utilize-available-screen-space/)

- **The work gets the space.** Full width, no max-width gutter on a working
  page.
- **Use one breakpoint system** (e.g. Material 3's window size classes) and
  name breakpoints by it, not by ad hoc pixel values.
- **Two panes from a wide breakpoint only**, and never a dense two-pane layout
  at a medium width.
- **Reposition and swap before you shrink.** A table that only gets narrower has
  not adapted.
- **Wide tables scroll inside their card**, and the page never scrolls
  sideways.
- **Density is correct for a register.** It is not an argument for going below
  the spacing steps.

## 6b. No deceptive or needy patterns

No popup on load, no interstitial, no "are you sure you want to leave" unless
typed work would be lost, and nothing preselected on the person's behalf. See
the `ux-laws` skill, Never a deceptive pattern.

## 7. Shared desks and sensitive data

- **The signed-in person is always visible**, and sign out is easy to find.
- **Never log a token, a password or a full API error object.**
- **Personal details are shown only to roles that need them**, as the API
  returns them. The client never unmasks or reconstructs what the API withheld.
- **No personal data in a URL** beyond record ids.
- **No extra lock screen.** The API decides session length.

## 8. Test in the browser, with the people

- **Run the screen in the browser** against a live API, at a desktop width and a
  narrower one, with the keyboard only, and at 200% zoom.
- **Where possible, watch a real user do a task without helping.** Until someone
  has, say so.

## Checklist (flows, access, navigation, tables, fields)

- [ ] No tour or promotion, and help appears at the moment of need
- [ ] Access decided by the API, gated by permission, refusals explained in plain English
- [ ] Every page stands alone from a pasted link, and URLs are short, readable and permanent
- [ ] Labels carry scent, links look like links, and links open in the same tab unless they say otherwise
- [ ] Navigation, then page, then tabs only inside a record, with shareable state in the URL
- [ ] Pages not infinite scroll, place kept on return, no carousel or auto-advance
- [ ] Tables support find, compare, view and act, with filters visible and removable
- [ ] Every field passes the input checklist, and formats are accepted liberally
- [ ] One breakpoint system, the work gets the space, no sideways page scroll
- [ ] Safe at a shared desk, with nothing sensitive logged or put in the URL
- [ ] Checked in the browser, and "untested with users" stated
