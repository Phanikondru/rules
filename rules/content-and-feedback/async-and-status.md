# Async actions and system status — the product never goes quiet

Applies to **every control that starts a request** and to every screen that
shows data or waits on something. Source:
[Visibility of System Status](https://www.nngroup.com/articles/visibility-system-status/)
(NN/g).

Which kind of message a status is (indicator, validation or notification), and
so which component carries it, is in `indicators-validations-notifications.md`.

A person cannot tell a slow request from a dead page. If the screen says
nothing, they click again (a second approval, a duplicate record) or leave
mid-save.

## Rule 1: a control that starts work shows it

Give the button a loading state and the dialog a busy state. Both block a
second click.

```tsx
const [saving, setSaving] = useState(false)

const handleSave = async () => {
  setSaving(true)
  try {
    await save()
  } finally {
    setSaving(false)
  }
}
```

- **Clear the flag in `finally`.** A failure must never leave a control
  spinning for ever.
- **Rows with their own actions get their own flag.** A single shared flag that
  disables every row while one row is busy is wrong. Allow on one request must
  not freeze the others.
- **A busy row control sets `aria-busy`** and ignores a second click.
- **A background call slow enough to notice** gets a visible signal near what
  it affects.
- Local-only actions (opening a dialog, changing a filter) need nothing.

## Rule 2: two kinds of waiting, two treatments

| What is happening | Show |
|---|---|
| A table or section is loading | A skeleton at the real row shape. Never a spinner in a table |
| Something the person started is running | The busy control, plus a sentence if it can take more than a few seconds ("Uploading photo 2 of 3") |
| The whole app is starting | A full-page spinner, and nothing else uses it |

**A skeleton is maintained with its table.** If a row's shape changes, update
its skeleton in the same change.

## Rule 3: an unreachable API is an error with a way back

Unless the product is built to work offline, when the API cannot be reached:

- **The section shows the error panel** (what failed, **Try again**).
- **Whatever was already on screen stays**, and the panel says it is showing
  the data as it was. A stale table and a missing one are different facts.
- **Typed input is never lost** when a save fails for lack of a connection.
- **Each section fails on its own.** One failing request does not blank the
  page.

## Rule 4: show what happened

After an action completes, the screen **states the resulting state**: the row's
pill changes, the count moves, the dialog closes onto the updated row. A button
that quietly re-enables tells nobody anything.

Prefer an inline, persistent line to anything that vanishes (see
`indicators-validations-notifications.md` on toasts).

## Rule 5: say what happens next

The committing button names the outcome ("Allow leave", "Close account"),
never "OK", "Submit" or "Confirm". Where the result is not obvious, the
dialog's description says it.

## Rule 6: "As of" lines and Refresh buttons are a project decision

Decide once whether pages draw a fetched-at time or a page-level Refresh
button, and record it in the style guide doc. One option: no page has either,
because a reload does the same and pages refetch when the window is looked at
again after going stale (rule 7). In that case show a timestamp only where the
record itself carries one (created, last seen), formatted with one shared
relative-time helper. Never invent one. An error panel keeps its Try again.

## Rule 7: refresh on the event, poll only what is caused elsewhere

- **Nav counts refresh when the thing they count changes here**: for example,
  raising or moving an item bumps a shared revision counter.
- **Poll only what happens outside the app** (live positions, remote events),
  and never a list the person is acting on.
- **Refetch when the window is looked at again** after it has gone stale.

## Rule 8: status fetches never break the screen

A failed count, badge or tile leaves that element empty ("no count rather than
a nought") and the rest of the page working.

## Rule 9: permission denied is not an error

A 403 takes the permission notice: plain muted text saying what the person
would need, in plain English. It never takes the danger panel, and the table it
replaces is not drawn.

## Rule 10: a record's status is a tracker

From NN/g's
[Status Trackers: 6 Guidelines](https://www.nngroup.com/videos/status-trackers/)
(Megan Brown). Records such as requests, leave or exits move through states
that somebody waits on.

- **Show the status where the action ended.** After raising or moving a
  record, the person sees its new status at once.
- **Reachable from where people look later**: the record's row, its detail
  view, and the person's own list.
- **Show the history in time order**: each state, who moved it, and when.
- **Say what is needed to find a record** (a number or a name) where search asks
  for it.
- **A "not yet" is not an error.** Something that has not happened yet says so
  and says when to look again.
- **Plain language, never the back-end state.** "Waiting for the supervisor",
  not `PENDING_L1`.

## Checklist

- [ ] Every control that starts a request shows busy state, cleared in `finally`
- [ ] Per-row actions have per-row busy state
- [ ] Tables load with a skeleton at the real shape, never a spinner
- [ ] Unreachable API: error panel with Try again, and existing data and input kept
- [ ] Completion states the result, and the commit names the outcome
- [ ] The project's decision on "As of" lines and Refresh buttons is followed
- [ ] No polling of a list being acted on; counts refresh on the event
- [ ] A failed count degrades to nothing; a 403 takes the permission notice
- [ ] Record status is visible where the action ended, with its history, in plain words
