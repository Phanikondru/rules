# Dense pages — many sections, much data, and how to make them scannable

Applies to **any page, sheet or record with many sections or a lot of data**:
a detail page, an overview, a long sheet, a settings page, a table with many
columns. Use it to optimise a page that has grown, or to ideate one that will be
long before it is built. Sources (NN/g):
[5 Formatting Techniques for Long-Form Content](https://www.nngroup.com/articles/formatting-long-form-content/)
(Huei-Hsin Wang and Megan Chan, 2023) ·
[Data Tables: Four Major User Tasks](https://www.nngroup.com/articles/data-tables/)
(Page Laubheimer, 2022).

`reading.md` decides how a block of text is laid out. `feature-value.md`
decides whether a thing should exist. `web-ux.md` §4 sets the table tasks. This
file decides **what to do when a page carries too much**: cut first, then
structure, then format.

## What the research found

**Long-form (over 1,000 words), tested on laptop and mobile.** People scan.
Formatting raises scannability, but it only works on content that was edited
first: essential, granular, condensable, plain and brief. Structure comes
before formatting: an overview, digestible chunks, layered disclosure, and
in-page links.

The five formatting techniques:

| Technique | Finding |
|---|---|
| **Summaries** | Key points up front (or as checkpoints) help people judge relevance. At the end they are rarely found. Set apart with a border or shading |
| **Bold and highlight** | No more than about 30% of the text. More slows scanning |
| **Bullets** | Help scanning when short. Long bullets need bold to carry them |
| **Callouts** | A paragraph made to stand out, for a statistic, quote, example or definition |
| **Visuals** | Informational ones simplify. Decorative and stock ones lengthen the page for nothing |

**Data tables** serve four tasks: find, compare, view or edit one row, act on
records. Findings that matter here:

- The first column is a **human-readable identifier**, never a generated id.
- Related columns sit **next to each other**, ordered by what people need first.
- **Active filters are visibly indicated.**
- A table larger than the screen **freezes its header** (and the identifier
  column when it scrolls sideways).
- Orientation aids: borders, zebra striping or row hover. Columns can be hidden
  or reordered cheaply, with the state visible.
- **Do not open a modal over the table** to view or edit a row. People read the
  neighbouring rows while they do it. Prefer a nonmodal side panel.
- **Avoid accordions** for row detail: they clean up badly, and non-adjacent
  rows cannot be compared.
- **Row actions suit one or two options.** More means batch actions: checkboxes
  and buttons above or below the table, with "select all" when whole-set actions
  are common.

## Mapping the findings to the product

Check which of these the product already has, and record the decision for the
ones it does not:

| NN/g finding | Typical implementation |
|---|---|
| Overview first | A tile row, count lines, a scope trail |
| Chunks | Section headings, cards, and tabs for a record's related lists |
| Callout | The warning and error panels, in place |
| Summary at the top | Tiles above the table. A page's answer is above the fold |
| Readable first column | The row subject, as a link |
| Active filters shown | Removable filter chips |
| Side panel, not modal | A side sheet over the list, with the row still marked |
| Frozen header | A sticky table header |
| Zebra striping | Optional. Borders and row hover can orient instead |
| Accordion | Not used on desktop (`web-ux.md` §4) |
| Column hide and reorder | A product decision, never a one-off |
| Batch actions with checkboxes | A product decision, never a one-off |
| In-page contents list | A product decision. Navigation and tabs usually split a record |

**Known gaps.** Where column hiding, batch actions or an in-page contents list
do not exist, ask for them only where the goal is real, and check a reference
product and the project's style guide first (`feature-value.md`, rule 4).

## Rules

### 1. Cut before formatting

Formatting a page that should be shorter is polish on the wrong problem.
For every section and every column, ask the four questions NN/g asks of
content:

- **Essential?** Does it change what the person does (`voice.md`, the five
  questions)? If not, remove it.
- **Granular?** Is it at the right level, or a detail that belongs one click
  deeper (a sheet, a tab)?
- **Condensable?** Can three lines become one value, or a paragraph a table?
- **Simple?** Is there a plainer word or a shorter form?

Also remove: a column that repeats one value, a tile that resolves itself, a
label that restates its heading, a second pill on a row.

### 2. Name the one decision, then order by it

The page's one decision leads (`ui-workflow.md`). Everything else is ordered by
how often it is needed, most used first, and related things sit together
(proximity before boundary).

- **The answer is first**: the tiles, the warning panel, then the first rows.
  Not a heading, a paragraph and a filter bar before any of them.
- **Order columns by the task**: identifier, then what is compared, then
  status, then the action last.
- **Group related columns** and keep a group's edge obvious with space, not a
  second header row.

### 3. Chunk, and layer

- **One idea per section**, with a heading whose first two words carry it
  (`reading.md`).
- **A record's related lists are tabs**, not a long scroll.
- **Detail goes deeper, not longer**: row, then sheet, then tab, then dialog
  (`feature-value.md`, rule 7). Never a longer row.
- **No accordion on a desktop page** for anything the task needs. A section is
  either shown or it is behind a tab.
- **More than about seven chunks on a page** is a finding (Miller, the `ux-laws` skill).
  Split by task into tabs or into another page, and give it a navigation entry
  only if users would look for it there.
- **A long page keeps orientation**: sticky table header, the title and scope
  visible on return, and section headings that read as a list on their own.

### 4. Summaries and checkpoints

- **Lead with the summary** of a long section: a count line ("3 of 14 waiting"),
  a tile, or a single sentence with the consequence first. Set apart from the
  body by placement and a card edge, not by a decorative box.
- **A summary is the server's figure**, never a tally of the rows below
  (`ui-workflow.md`, Honest screens).
- **A summary at the end of a page is not found.** Put it first.

### 5. Emphasis is a budget

- **Bold on no more than about 30% of a block's text**, and fewer in a table.
  Values stand out as values, so a person scanning a column finds them. If
  everything is emphasised, nothing is.
- **Bullets are short.** A bullet longer than a line carries its key word in a
  heavier weight, or becomes a table row.
- **A callout is for one thing that changes the reading**: a doubt, a limit, a
  definition. It is the warning or error panel in place, never a new tinted
  box, and never more than one or two on a page.
- **Type steps stay within the project's small set of sizes**
  (`visual-design.md`). Weight and lightness do the rest.

### 6. Visuals carry information

- **A chart, map, photo or tile is here because it shows what a sentence
  cannot.** No decorative image on a working page (`visual-design.md`).
- **An image that lengthens the page for nothing is removed.**

### 7. A table with much data, by the four tasks

- **Find.** The first column is the row subject in words users use, never an
  id. Search and filters sit above the table, and every applied value is a
  removable chip with a count of matches.
- **Compare.** Numbers are right-aligned in tabular numerals. The header
  carries the word so the cell carries the figure. The header is sticky, and a
  table too wide for its card scrolls inside it with the cut-off column
  visible (`scroll-fading.md`, rule 3). The identifier column stays in view
  where the table scrolls sideways.
- **View one.** A side sheet over the list, never a modal and never an inline
  accordion. The chosen row stays marked, and closing returns to the same row.
- **Act.** One or two actions live on the row. Three or more go in the row
  overflow menu, the destructive one last and confirmed. If batch actions are
  not in the product, say so, and route the request through
  `feature-value.md`.
- **Pages, with the range stated** (`1 – 30 of 743`), never infinite scroll.

### 8. Ideating a dense page: shapes, not a shape

When the request is "we need to show all of this":

1. **List every item** the page must carry, with its source (the API field, or
   "not returned yet").
2. **Sort each into**: leads, supports, deeper, or removed. Say why each
   removed one goes.
3. **Offer three shapes** with one recommendation: for example one page with
   tiles and a table, a page with a tab per task, or a table with a sheet for
   detail. Each is built only from the components that exist.
4. **Name the first slice** that ships alone and answers the one decision.
5. **Say what is untested** with users.

## Checklist (every long or data-heavy page)

- [ ] Every section and column passed: essential, granular, condensable, simple
- [ ] The one decision leads, and the answer is above the fold
- [ ] Sections are chunked, related lists are tabs, and nothing needed hides in an accordion
- [ ] The summary is first, the server's figure, and carries its age
- [ ] Emphasis is about 30% or less, bullets are short, callouts are few and are panels
- [ ] No decorative visual, and every visual shows what words cannot
- [ ] Table: readable first column, related columns together, sticky header, chips for filters, right-aligned figures
- [ ] Row detail opens in a side sheet, and actions are one or two on the row, the rest in overflow
- [ ] Gaps (batch actions, column hide, contents list) named, not built ad hoc
- [ ] "Untested with users" stated
