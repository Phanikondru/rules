---
name: ux-laws
description: Heuristics from Laws of UX (lawsofux.com) + Laws of UI (uilaws.com) — the psychology and visual principles behind good interface design (Fitts, Hick, Jakob, Miller, Gestalt grouping, hierarchy, contrast, white space, etc.). Use ALONGSIDE ui-ux-principles whenever designing, reviewing, or deciding UI: layout, navigation, CTAs, menus, density, forms, redundancy/affordance questions. Reach for it to justify a design decision with a named law.
---

# Laws of UX & UI

Apply these as a **decision + critique lens** on any UI work, paired with the
`ui-ux-principles` checklist. `ui-ux-principles` = *what* to check (a11y, contrast,
states); this skill = *why* a design works, named laws to reason and argue with.

> Sources: [Laws of UX](https://lawsofux.com/) (Jon Yablonski) · [Laws of UI](https://www.uilaws.com/).
> When a UI choice is contested, cite the specific law(s) for/against — don't hand-wave.

## How to use this skill
1. **Designing** → run the relevant laws as a generative checklist (hierarchy, grouping, target size, choice count).
2. **Reviewing/critiquing** → name the law a screen violates ("too many top-level choices → Hick's Law"), and the fix.
3. **Deciding between options** (e.g. "do we need this second button?") → weigh the competing laws explicitly and give a recommendation, not a survey.
4. Prefer the **fewest** laws that actually decide the question. Don't list all 30.

---

## Laws of UX — psychology (lawsofux.com)

**Cognitive load / memory**
- **Cognitive Load** — mental effort to use an interface; cut extraneous load, spend the budget on the task.
- **Miller's Law** — ~7±2 items in working memory; chunk content into small groups.
- **Working Memory** — temporary store; don't force users to hold state across steps — show it.
- **Chunking** — break info into meaningful groups (phone numbers, nav sections, form sections).
- **Tesler's Law (Conservation of Complexity)** — irreducible complexity exists; the *system* should absorb it, not dump it on the user.

**Decisions & attention**
- **Hick's Law** — decision time grows with number + complexity of choices; reduce/段 stage options, highlight recommended ones.
- **Choice Overload** — too many options overwhelms; curate, default, progressively disclose.
- **Selective Attention** — users tune out anything off-goal (incl. ad-like UI / banner blindness).
- **Von Restorff (Isolation) Effect** — the item that differs is remembered; make the primary action visually distinct (but only ONE).
- **Serial Position Effect** — first & last items are best recalled; put key actions/nav at the start or end of a series.

**Interaction & speed**
- **Fitts's Law** — time-to-target ∝ distance ÷ size; make primary targets big and near; large click areas, edges/corners are "infinite" size.
- **Doherty Threshold** — keep system response < 400ms (or show progress/optimistic UI) to keep users in flow.
- **Flow** — protect focused immersion; avoid needless interruptions, modals, context switches.
- **Goal-Gradient Effect** — motivation rises near the goal; show progress (steppers, "2 of 5"), front-load apparent progress.
- **Zeigarnik Effect** — unfinished tasks nag; surface incomplete states (drafts, checklists) to pull users back.

**Expectations & forgiveness**
- **Jakob's Law** — users expect your UI to work like the others they know; honor conventions before inventing.
- **Mental Model** — match the user's existing model of how things work; reduce the gap.
- **Postel's Law** — be liberal in what you accept (input), conservative/robust in what you output; forgiving forms.
- **Paradox of the Active User** — users won't read docs; design to be learnable in-action.
- **Peak-End Rule** — experience judged by its peak + ending; nail the highest-friction moment and the finish (success states, confirmations).

**Form & perception (Gestalt + simplicity)**
- **Aesthetic-Usability Effect** — pretty is *perceived* as more usable (and earns patience for minor flaws); polish matters.
- **Law of Proximity** — near elements read as grouped; use spacing to group, not just borders.
- **Law of Common Region** — a shared boundary (card/section) groups elements strongly.
- **Law of Similarity** — visually similar elements read as related/same type.
- **Law of Uniform Connectedness** — visually connected elements (lines, containers) feel most related.
- **Law of Prägnanz (Simplicity)** — the eye resolves complexity into the simplest form; favor simple, regular shapes/layouts.

**Process / strategy**
- **Occam's Razor** — remove until it breaks; fewest elements/assumptions that still work.
- **Pareto Principle (80/20)** — ~80% of use comes from ~20% of features; optimize those first.
- **Parkinson's Law** — work expands to fill time; constrain steps/inputs, autofill, sane defaults.
- **Cognitive Bias** — account for systematic judgment errors (anchoring, framing) in how you present choices/defaults. Use this to protect users, never to steer them: nothing picked for them, declines neutral.
- **Priming** ([NN/g](https://www.nngroup.com/articles/priming/)) — what a person has just seen shapes what they expect and do next. A scope trail primes reading figures as that scope's; a red tile primes alarm, so a zero is never red; a pre-filled value primes acceptance, so say it was pre-filled. In usability tests, never use the screen's own words in the task, or the test measures word matching.

## Laws of UI — visual craft (uilaws.com)
- **Typography Hierarchy** — clear size/weight steps guide reading order; one type scale.
- **Contrast** — what stands out gets attention + memory; ensure the primary action/figure has the most contrast (and meets WCAG).
- **White Space** — negative space improves focus, readability, perceived quality; don't fear emptiness.
- **Consistency** — repeat patterns (spacing, components, terminology) across screens; inconsistency reads as low quality.
- **Color Theory** — color carries emotion/meaning; use a restrained, harmonious, semantic palette.
- **Symmetry** — symmetrical elements read as one unit; use for balance/calm.
- **Rule of Thirds** — place key elements along a 3×3 grid for balance.
- **Proximity / Closure / Continuity / Symmetry** — Gestalt visual grouping (mirror the UX Gestalt laws above) — arrangement implies relationship; the eye completes shapes and follows lines.
- (Shared with UX: **Fitts's**, **Hick's**, **Jakob's** — same definitions.)

---

## Never a deceptive pattern
NN/g ([Deceptive Patterns](https://www.nngroup.com/articles/deceptive-patterns/)) defines one as a design that gets people to act by "deceiving, misdirecting, shaming, or obstructing". Even without a commercial motive, the same shapes appear by accident. None is allowed:
- **Obstruction** — the safe action is one click and the opposing one is buried.
- **Visual or wording tricks** — a destructive button styled as the safe one, a double negative, buttons that swap places between dialogs.
- **Nagging** — a dismissed notice that returns on every load.
- **Emotional manipulation** — shaming copy on a decline ("Are you sure you want to leave the gate uncovered?").
- **Sneaking or preselection** — a checkbox ticked for the person, a default filter applied without a visible chip, a pre-filled value not marked as such.
- **Sludge** — extra steps or a dialog in front of a routine, safe action.

Before shipping, ask NN/g's questions: could someone share or change more than they meant to, misread a choice from how it is shown, miss an option, feel rushed, or feel shamed for declining? Any yes is a defect.

## When laws conflict
Resolve in this order and say which one decided:
1. **The brief and honesty** (what the product must not fake or hide).
2. **The project's design system / style guide.** A law justifies a spec; it does not change one quietly.
3. **The law that protects the task**: Hick, Fitts, Cognitive Load, Doherty.
4. **The law that polishes it**: Aesthetic-Usability, Prägnanz, Von Restorff.

Common tensions:
- **Density vs. Cognitive Load** — dense is correct for a register of records; clutter is not. Cut columns that repeat a value.
- **Jakob vs. the brief** — an icon-only convention loses to a glyph plus a word wherever there is room.
- **Zeigarnik vs. Flow** — show unfinished work where the person already looks, but never interrupt to say it.
- Apply every law for the real reader (e.g. someone who does the task dozens of times a day), not a first-time visitor. Record a decision that changes the style guide with its law, in one clause.

## Quick "do we need this?" rubric (redundancy / affordance calls)
When asked whether an element (a second button, an extra menu, a duplicate CTA) is needed:
- **Jakob's Law** — do peer products (Stripe, Linear, Ramp…) keep both? Convention is evidence.
- **Fitts's + Selective Attention** — is the page's *primary job* reachable as a big, obvious, in-context target — not hidden in a global/secondary affordance?
- **Hick's Law** — does the in-context control offer fewer, scoped choices (faster) vs a global menu's longer list?
- **Von Restorff** — is there exactly ONE clear primary action per view? Two competing primaries is the real smell, not two *entry points* serving different jobs.
- **Occam's Razor** — if an element serves no distinct job the other already covers in-context, cut it.
- Verdict pattern: a **global** shortcut (always-available, cross-app) and a **page-level primary CTA** (contextual, scoped, discoverable) are *complementary, not redundant* — keep both. Two affordances doing the *same job in the same context* → collapse to one.

## Output discipline
- Tie each recommendation to a **named law**; don't assert taste as fact.
- Give a **recommendation**, not an exhaustive law dump.
- This skill informs *why*; combine with `ui-ux-principles` (a11y/states/perf) and the project's design tokens/reference rules for the *how*.
