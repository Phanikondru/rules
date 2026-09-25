# Voice — what the product says

Applies to **every string a person reads**: page titles, buttons, column
headers, hints, empty states, errors, dialogs, status pills, permission text.

## Who we are talking to

Define this once per project, in the style guide doc (e.g. `DESIGN.md`): who
reads the screen, how fluent they are in the language, what they are doing when
they read it (working a queue, browsing, in a hurry), and what register the
context calls for (serious, friendly, formal). Every choice below follows from
that. The defaults here assume non-technical readers, some reading in a second
language, who act on what the screen says.

## Rules

1. **Plain words, short sentences.** "Waiting" over "Pending approval". Say it
   the way a colleague would.
2. **Sentence case everywhere**, except any deliberate overline style. Full
   stops on sentences. No exclamation marks and no emoji. Buttons, tabs and
   pill labels take no full stop.
3. **Name the outcome on the button.** "Allow leave", "Close account",
   "Sign out". Never "OK", "Submit", "Yes" or "Confirm".
4. **A dialog's title is the question** ("Close this account?"), and its
   description says the consequence ("New activity stops. Everything already
   recorded stays.").
5. **Results state the new state**, not "Success".
6. **Errors say what happened and what to do**, in that order.
7. **The API's own wording is kept when it is useful** ("Too many failed
   attempts") because it carries the one thing the person needs. What never
   reaches the screen: field names from the code, error codes, stack text, or a
   raw error object. Field messages are mapped to the form's words.
8. **An unreachable API is said plainly**, with what to do next. It does not
   blame the person.
9. **Empty states** have a glyph, a heading line and one sentence, plus the
   action if there is one. A clean result says so ("Everything is up to
   date."). An empty filter says so ("Nothing matches those filters.").
10. **Permissions in plain English**: "Can manage contracts (create, edit,
    end)", never a permission key.
11. **One word per thing.** Check the existing copy files before introducing a
    new word for something that already has one. "Complaint" must not become
    "report" or "issue" on another screen. A word the code uses is not
    automatically the word on screen.
12. **Declines are neutral.** "Cancel", "Keep it", "Not now". Never guilt.
13. **Ask one thing, positively.** No double negatives.
14. **Never soften a record.** If an action changes a person's record, pay or
    access, the dialog says so.
15. **The plain register, never the enum**: Waiting, Allowed, Refused,
    Withdrawn. Not `PENDING`, `APPROVED`.

## Tone

On NN/g's [four dimensions of tone](https://www.nngroup.com/articles/tone-of-voice-dimensions/),
place the product on each axis and write the position down:

| Dimension | Decide |
|---|---|
| Formal ↔ casual | Formal reads as plain with no slang. Avoiding contractions helps second-language readers |
| Serious ↔ funny | Serious contexts never joke |
| Respectful ↔ irreverent | Default to respectful |
| Matter-of-fact ↔ enthusiastic | Matter-of-fact: good news is stated, not celebrated |

Pick three or four tone words and a few anti-tone words. (Example: *plain,
calm, exact, respectful* against *chirpy, cute, salesy, alarmist,
bureaucratic*.)

- **A calm senior colleague**: respectful, direct, never cute.
- **Talk to the person** ("Type the mobile number"), not about the system.
- **Never blame.** "That password did not work", not "You entered a wrong
  password".
- **Never rush or scare.** No "Warning!", and no "Immediately".

## Plain language

1. **One idea per sentence**, about ten to fifteen words. No semicolons, and no
   dashes joining clauses.
2. **Name the real thing**: "mobile number", "photo", "phone". Not
   "identifier", "entity", "record type".
3. **Common verbs**: type, pick, click, send, save, allow, refuse. Not enter,
   select, submit, proceed, initiate.
4. **Numbers as figures**, times and dates in the reader's own format and time
   zone, counts as "3 of 14".
5. **Keep the words people already use**: sign in, password, OTP.
6. **Test it aloud.** If it sounds odd said across a desk, rewrite it.

### Words to use (example glossary)

Keep a glossary like this in the project; these rows are examples of the shape.

| Use | Not |
|---|---|
| Type | Enter, input |
| Pick | Select, choose from the following |
| Save | Submit, persist |
| Mobile number | Phone identifier, username |
| Waiting | Pending, in queue |
| Allow, Refuse | Approve, Reject |
| Remove | Delete, archive (when that is what the person means) |
| Try again | Retry the operation |

## Short copy: headings, commands, links and errors

From NN/g's [UX Writing Study Guide](https://www.nngroup.com/articles/ux-writing-study-guide/).

- **Headings and page titles are microcontent.** They make sense out of
  context and lead with the key word. The browser tab title names the page.
- **Command labels say the outcome** (rule 3). Never "Get started", "Learn
  more", "Click here" or "Details" alone. A link says where it goes
  ([A Link Is a Promise](https://www.nngroup.com/articles/link-promise/)):
  "Open overdue items", "View on map", "See Ravi Kumar's leave".
- **A link never surprises.** It goes where its words say, and a link that
  downloads or leaves the product says so.
- **Error messages** follow NN/g's
  [error-message guidelines](https://www.nngroup.com/articles/error-message-guidelines/):
  they are visible beside the problem, say what happened in human words, say
  how to fix it, keep the input, and never blame.
- **Numbers as numerals**: "3 of 14", never "three of fourteen".
- **Say who did what** on a record (who raised it, who allowed it, and when).
  Anonymous changes are not trusted.
- **Specialist words are allowed only where the readers use them** in their own
  work. They are never words from the code.

## What to show: five questions for every line

From NN/g's research (sources below). A line stays only if it passes all five.

1. **Is it something the person sees and cares about**, not how the system
   works?
2. **Does it change what they do**, or answer a worry they really have?
3. **Is it true right now, and specific?** A time, a place, a person.
4. **Is the main point first, and said only once?**
5. **Does it stay only as long as the situation it describes?**

Sources (NN/g):
[Visibility of system status](https://www.nngroup.com/articles/visibility-system-status/) ·
[Aesthetic and minimalist design](https://www.nngroup.com/articles/aesthetic-minimalist-design/) ·
[Lower-literacy users](https://www.nngroup.com/articles/writing-for-lower-literacy-users/) ·
[Inverted pyramid](https://www.nngroup.com/articles/inverted-pyramid/) ·
[How users read on the web](https://www.nngroup.com/articles/how-users-read-on-the-web/)

## Where copy lives

Strings that map from a status, code or state belong in one copy module per
feature, not scattered through pages. One-off page text may stay in the page.
Field-name mapping for API errors lives in one place with the error handling.

## Checklist

- [ ] Every line passes the five "What to show" questions
- [ ] Plain words, sentence case, no exclamation marks or emoji
- [ ] Words from the project glossary, with no system nouns or enum values
- [ ] Buttons name the outcome, and dialog titles are the question
- [ ] Errors say what and what next, with no field names or codes
- [ ] Terms match the existing copy usage
- [ ] Declines neutral, questions positive, and the copy matches what the button does
