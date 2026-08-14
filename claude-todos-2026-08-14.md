# TODOs — Ubiquitous Language / ERD Sync (2026-08-14)

Review notes from cross-checking `design-docs/01-ubiquitous-language.md` against
`design-docs/02-entity-relationship-diagrams.md` and `notes.md`, before starting
more detailed domain modeling.

## Overall state

- `00-product-principles.md` — done, solid.
- `01-ubiquitous-language.md` — actively being worked. This is the one to polish.
- `02-entity-relationship-diagrams.md` — mostly in sync, but drifted from the
  language doc in a few concrete spots (below).
- `03-domain-model-specifications.md` — just a template, as expected.
- `04-user-stories.md`, `05-data-models.md` — empty, as expected.

## Ubiquitous Language doc ↔ Diagram sync

1. **Undefined terms that appear in diagrams but have no entry in the language doc.**
   The MorningLog/EveningLog ERDs reference entities the doc never formally
   defines: `SleepRecord`, `Mood`, `ObstacleAndResponse` (as a join concept),
   `SignalReview`, `GratitudePromptAndResponse`, `ReflectionPromptAndResponse`,
   `GratitudePrompt`, `ReflectionPrompt`. `Signal`/`Noise`/`Obstacle` got this
   treatment already — these deserve the same.

2. **`SignalReview` is undefined and unresolved.**
   It shows up in the EveningLog diagram (`EveningLog }|--|{ SignalReview`) but
   there's no definition, and `notes.md` has an open question — "What does
   review Signal every evening mean?" — that's literally blocking this. There's
   also a matching `<!-- TODO -->` comment left inline in the doc. Resolve the
   concept first, then define the term.

3. **`Operation → Task` relationship is missing from the doc.**
   The diagram has `Operation ||--o{ Task : "creates and owns"`, but Operation's
   **Relationships** section only says "Operations can support Outcomes."
   Project and Commitment both got their Task-ownership relationship written
   out — Operation didn't.

4. **`Task`'s Relationships section is completely empty.**
   Despite three different parents owning it in the diagram (Operation,
   Project, Commitment) and a Rule saying "Tasks cannot exist without their
   parent," there's nothing in Task's own Relationships section stating who
   that parent is.

5. **`ReviewObservation`'s Relationships are vague compared to the diagram.**
   Doc says only "references Vision and Entry Domain objects." The actual ERD
   is specific: Focus, Outcome, Operation, Project, Commitment (general
   diagram) plus Vision and Log (domain-specific diagrams). Decide: does the
   language doc state the general pattern once, or enumerate per Review
   subtype like the diagrams do?

6. **Duplicated paragraph — looks like a copy/paste error.**
   The `ReviewObservation` section contains this paragraph, verbatim, from the
   `MorningLog` section above it:
   > "MorningLogs will remind users of their active Focuses and their
   > scheduled Commitments and Tasks for the day..."

   Doesn't belong under ReviewObservation — delete or replace with what
   ReviewObservation actually does.

7. **No inheritance diagram for Focus, unlike Entry.**
   There's a `classDiagram` showing `Entry <|-- Log <|-- MorningLog/EveningLog`
   and `Entry <|-- Review <|-- Weekly/Monthly/QuarterlyReview`. The doc's
   heading structure implies `Focus` has the same relationship to
   `WeeklyFocus`/`MonthlyFocus`/`QuarterlyFocus`, but there's no diagram
   showing it.

8. **`Vision` missing from the general Review-and-Focus ERD.**
   The doc says ReviewObservation can target "a member of the Vision Domain,"
   but the general diagram's ReviewObservation target list omits `Vision` — it
   only shows up later, in the QuarterlyReview-specific diagram.

## Cleanup inside the doc itself

9. **Three inline `<!-- TODO -->` comments still unresolved** — two say "move
   this to a new doc" (the MorningLog/EveningLog prose blocks), one asks "What
   does it mean to review Signal items?" Decide where that prose content
   actually belongs (maybe `03-domain-model-specifications.md`, once it's
   built out) and resolve or delete each.

10. **Prose-only fields under ReviewObservation aren't promoted to real terms.**
    `Reflection`, `Lessons`, `Adjustments`, `Score` are mentioned only in a
    paragraph, with a `<!-- TODO: these need better names -->` comment
    attached. Compare to how `Signal`/`Noise`/`Obstacle` were pulled out as
    first-class sub-terms — these probably deserve the same.

11. **Fold in (or explicitly defer) the open questions in `notes.md`.**
    Four questions are sitting there unresolved (Signal review meaning, Week
    Scores in WeeklyReviews, restructuring WeeklyFocus into a list of points,
    whether QuarterlyReview should reference Projects). At least one of these
    blocks item #2 above.

## Copy editing (quick pass, low risk)

- Title: "Ubiquitous **Languge**" → "Language"
- "OLOS **environent**" → "environment"
- Intro says "**Entries** Domain" but the heading says "Entry Domain" — pick one
- Operation definition: "What am **continuously I** responsible for?" → "What
  am I continuously responsible for?"
- Scattered typos: "**defintion**" (Project), "**commited**" (Commitment),
  "**continiously**" (Review), "**accoutability**" (Review And Focus intro),
  "**Quaterly**" (MorningLog prose), "**activites**" (Agenda), "**seperate**"
  (EveningLog TODO comment)

## One structural judgment call

A lot of terms still have empty **Distinction**/**Rules**/**Relationships**
sections (Vision, Commitment, Log, Review, WeeklyReview, MonthlyReview,
QuarterlyReview, FocusPoint, Metric, MonthlyFocus, QuarterlyFocus, etc.).
Decide term-by-term: is "empty" actually correct here (nothing distinguishes
this term / no rules apply), or is it just unfinished? Silently-empty sections
are ambiguous to a future reader — an explicit "N/A" is different from "not
written yet."

## Suggested order of attack

1. Resolve #2 (Signal review) and #11 — blocking items.
2. Fix #1 and #6 — factual gaps/errors.
3. Fix #3, #4, #5, #7, #8 — diagram-sync.
4. Address #9, #10.
5. Typo pass last.
