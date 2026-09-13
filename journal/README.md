# OLOS, Run By Hand

This folder is a **manual implementation of the OLOS domain model** — the system
from `design-docs/` operated with Apple Calendar, Apple Reminders, and markdown
files, with no app in between.

Two reasons it exists:

1. **To organize a life.** The design is good enough to use now. Waiting for the
   app to exist is waiting for nothing.
2. **To settle the design.** `design-docs/03-domain-model-specifications.md` ends
   with a dozen Open Questions that can't be answered from a chair. Running the
   system by hand for a quarter answers most of them with evidence instead of
   guesswork — see [What This Run Is Testing](#what-this-run-is-testing).

Everything in `journal/` is **method** — templates, conventions, calendar
anchors. It is committed and publishable. Everything personal — actual entries,
Visions, Outcomes, habits, prompts — lives in a **separate private repo**
(see [SETUP.md](SETUP.md)), because Product Principle 8 says user data is never
shared and this repo is aimed at TestFlight.

---

## Where each domain object lives

| OLOS object | Surface | Representation |
|---|---|---|
| **Vision** | markdown | `system/01-visions.md`, one `##` section each |
| **Outcome** | markdown | `system/02-outcomes.md`, grouped under its Vision |
| **Operation** | Reminders + markdown | A **list** inside the `OLOS` list group; defined in `system/03-operations.md` |
| **Project** | Reminders + markdown | A **section** inside its Operation's list; defined under that Operation |
| **Commitment** | Reminders | A **recurring reminder** tagged `#commitment`, in its Operation's list |
| **Task** | Reminders | A reminder in its parent's list/section |
| **ScheduleItem** | Calendar | An event on the `OLOS Blocks` calendar |
| **Signal** | markdown + Calendar | Declared in the daily log; blocked as a `★`-prefixed event |
| **SleepRecord** | markdown | Front-matter `bed:` / `wake:` in the daily log |
| **Obstacle / Response** | markdown | `Obstacle → Response` section of the daily log |
| **MorningLog / EveningLog** | markdown | One file per day, `daily/YYYY-MM/YYYY-MM-DD.md`, two sections |
| **Weekly/Monthly/QuarterlyReview** | markdown + Calendar | `reviews/…`, prompted by a recurring anchor event |
| **Focus / FocusPoint / Metric** | markdown + Calendar | `system/04-focus.md`, mirrored as an all-day Calendar banner |
| **Prompt** | markdown | `system/06-prompts.md` (seeded from the old `docs/journal/.local/`) |

### Deliberately not modeled

- **Agenda** — descriptive only, per `03`. It is "today's events on `OLOS Blocks`."
- **Noise** — descriptive only. Nothing is logged.
- **Entry / Log / Review / Focus (abstract)** — no file of their own.
- **Quarter** — the calendar provides it.

---

## Conventions

### Reminders

```
OLOS  (list group)
├─ Health              ← Operation (list)
│   ├─ (no section)    ← Tasks owned directly by the Operation
│   ├─ § Fix sleep     ← Project (section)
│   └─ § Cut to 12%    ← Project (section)
├─ School
│   └─ § Capstone
└─ OLOS
    └─ § Journal v1
```

- **Tag `#commitment`** on every recurring reminder. A Smart List filtered to
  `#commitment` is your Commitment register for the WeeklyReview.
- **Tag `#o-<slug>`** on a Project section's anchor task, or on a Commitment, to
  record which Outcome it *supports*. Support is informational only — it never
  changes a status (`03`, Outcome § Assumptions).
- **Never create a Reminders list for a Project.** Projects are finite;
  lists are not. Sections die quietly, lists accumulate.

### Calendar

Two calendars:

| Calendar | Holds |
|---|---|
| `OLOS Rituals` | The recurring Morning/Evening/Review anchors + Focus banners |
| `OLOS Blocks` | ScheduleItems — the actual time-blocks |

ScheduleItem titles encode what they schedule, so evening reflection is
mechanical:

| Prefix | Schedules |
|---|---|
| `★` | a Signal |
| `⟳` | a Commitment |
| `·` | a Task |

### Files

```
daily/2026-09/2026-09-13.md
reviews/weekly/2026-W38.md
reviews/monthly/2026-09.md
reviews/quarterly/2026-Q4.md
system/01-visions.md … 06-prompts.md
```

---

## The four loops

### Daily — Morning (~10 min)

1. Open today's file from `daily/00-daily-template.md`.
2. Sleep and feeling.
3. Read `system/04-focus.md`. Copy the three active Focus statements into the log.
4. Check Reminders `Today` and Calendar for what is already committed.
5. **Declare Signal.** The things that, if nothing else happens, still made today
   count.
6. Adopt or kill anything pushed from last night.
7. **One Obstacle → Response.** `If <specific thing> then I will <specific thing>`.
8. **Time-block the Signal** in `OLOS Blocks`. If it has no block, it is not a
   priority — it is a wish.
9. Morning questions.
10. Do not edit this section again today. It is a frozen snapshot (`03`,
    MorningLog § Open Questions — dev answer). Tasks that appear later in the day
    go straight into Reminders and Calendar, not into the MorningLog.

### Daily — Evening (~10 min)

1. Same file, `## Evening`.
2. Feeling.
3. **Signal review** — each item: Complete / Push / Won't do. A Signal may be
   pushed at most twice; on the third day it must be done or killed.
4. **Obstacle review** — did it show up, did the response hold.
5. **Resolve unfinished Tasks** — complete, reschedule, or abandon. Nothing
   scheduled for today is allowed to stay silently open (`03`, Task § Open
   Questions — dev answer).
6. Habits checklist.
7. Evening questions.

**Every review is 30 minutes.** Each template carries a per-section budget. See
[rule 6](#6-every-review-is-30-minutes-observations-are-capped-at-three) for how
that is enforced and why it has to be.

### Weekly — Sunday, 30 min

Reviews execution. Secondary evidence — Logs, Signal counts, Commitment
kept-rate, Project movement — is swept as **counts, not prose**. Then exactly
**three** observations, chosen by rule: the previous WeeklyFocus, the worst-kept
Commitment, and the Project that most needed to move.

Output: one **WeeklyFocus** (max 3 FocusPoints) into `system/04-focus.md`, a
Calendar banner for the coming week, and a five-line **Roll-up** block.

### Monthly — last Sunday, 30 min

Reviews progress. Evidence is the four weekly **Roll-up** blocks — twenty lines,
pasted in. The weekly files are never reopened and the daily logs are never
touched. Three observations: the previous MonthlyFocus, the Outcome that moved
most, the one that should have moved and didn't. Output: a **MonthlyFocus** and
a Roll-up block of its own.

### Quarterly — last Sunday of the quarter, 30 min

Reviews direction. Evidence is the three monthly Roll-ups. The two questions from
`notes.md` come **first**, before any observation hardens into a story:

> What should exist that doesn't? What exists that no longer should?

Then **one observation per Vision** plus the previous QuarterlyFocus — a fixed
set, not a chosen one. Then the direction sweep: retire Visions, abandon
Outcomes, archive Operations. Output: a **QuarterlyFocus**.

This is the one budget that scales, and it scales with Vision count alone. Three
Visions is 30 minutes; five is 45, and the fix is fewer Visions.

The design review — ruling on `design-docs/03` Open Questions from a quarter of
System notes — is **not** part of this. It is engineering work on OLOS and lives
as a Task under the OLOS Operation.

Reviews nest bottom-up on shared Sundays: weekly 15:00, monthly 15:45, quarterly
16:30. The lower review's Roll-up *is* the higher review's evidence, which is the
only reason the higher ones fit in 30 minutes.

---

## Rules chosen for this run

The design docs contradict themselves in four places. Rather than block, each is
resolved here with a rationale and a recheck trigger. These are *operating*
decisions for the manual run, not amendments to `design-docs/`.

### 1. Signal minimum is 1, target is 3

- `01-ubiquitous-language.md`: "each MorningLog must declare at least one Signal item"
- `docs/journal/features/01-…`: "Prompt for Signal (Mandatory | min 3, max 5)"
- `03` § Signal raises this as an Open Question and leaves it.

**Decision: min 1, max 5, aim 3.** Product Principle 3 is "progress lies in
consistency, not in perfection." A hard minimum of 3 on a bad day means skipping
the entry entirely, which is the failure mode that kills journals — and a
skipped entry produces no data at all, while a one-Signal entry produces some.
**Recheck:** if across a quarter you never declare fewer than 3, the hard
minimum is free and should be enforced in v1.

### 2. Obstacle → Response minimum is 1

- `03` § MorningLog: "Creates/owns **zero or more** ObstacleAndResponse"
- `03` § ObstacleAndResponse: "**Mandatory ≥1** per MorningLog (see MorningLog's
  Assumptions)" — and MorningLog's Assumptions say nothing about it.
- The feature doc says min 3, max 5.

The same contradiction exists verbatim between `03` § EveningLog ("zero or more
PromptAndResponse") and `03` § PromptAndResponse ("Mandatory ≥1 per EveningLog,
see EveningLog's Assumptions" — which read "None"). Both are drafting bugs in
`03` worth fixing at the source.

**Decision: exactly 1 required, more allowed.** Three forced obstacles a day
produces invented filler by week two, and filler is worse than nothing — it
teaches you to not mean what you write. **Recheck:** count how often the single
obstacle is real.

### 3. Habits are not Reminders

`docs/journal/.local/habits.md` has twelve entries. Twelve recurring reminders
firing daily is noise, and noise is the thing this system exists to suppress
(Principle 6: calm, never overwhelming). They are a **checklist in the evening
log**, matching the design decision already recorded in
`docs/journal/design-decisions.md` ("Habits are displayed before questions…
less cognitive load"). Only a behavior that needs a *time-block* or a *specific
day* becomes a Commitment in Reminders.

This makes habits and Commitments distinct in practice even though the
ubiquitous language would class both as Commitments. **Recheck:** if a habit
keeps failing, promote it to a Commitment with a real block.

### 4. Evening questions rotate; they are not all answered nightly

`docs/journal/features/01-…` says "for every question: list one question per page
and await input." There are seven evening questions. Seven written answers, plus
a twelve-item habit checklist, plus Signal review, obstacle review, loose ends
and Commitments, is a forty-minute evening — and a ritual long enough to dread
is a ritual you stop performing.

**Decision: the School question nightly, plus one from Emotions and one from
Future, rotating.** Three honest answers beat seven dutiful ones.

**Recheck:** this is a real constraint on v1's design. If rotation works, the app
needs prompt *scheduling* (daily / rotating / weekly) rather than one flat list —
which `03` § Prompt does not currently model at all.

### 5. Weekly Focus is capped at 3 FocusPoints

`03` requires at least one and sets no upper bound. A Focus that lists eight
things is a task list, and `03` § Focus explicitly says a Focus "should be short
enough that the user could recite it from memory during a MorningLog days
later." Three is the recitable ceiling. Monthly and quarterly: 2.

### 6. Every review is 30 minutes; observations are capped at three

The first version of these templates had no observation cap. `03` says a
WeeklyReview's observations may evaluate "a Project, a Commitment, or the
previous WeeklyFocus" — and the templates read that list of *eligible target
types* as the *required target set*, so every Project and every Commitment got
its own five-field observation.

Against a real inventory that is unworkable. After the Founding Session there
are 6 Operations, ~10 Projects and ~21 Commitments, which made the WeeklyReview
**32 observations — close to two hours, 52 times a year.** Monthly came to 19
observations, quarterly to 11, each on top of re-reading every review beneath it.

The spec never asked for this. ReviewObservation is `||--o{` — **zero or more**,
never exhaustive. Thirty observations produce thirty shallow paragraphs and no
insight; the breadth actively destroys the thing reviews exist for.

**Decision, in four parts:**

1. **Three observations per review.** Not four.
2. **Selection is mechanical, never deliberated** — each template states the
   rule. Deliberating over *what* to observe is itself a cost, and it is the
   cost that makes people skip the session.
3. **Breadth moves to aggregate sweeps.** Commitments get one kept-rate line and
   only the worst is observed. This extends the treatment `03` already gives
   Tasks — "secondary evidence… not a direct ReviewObservation target" — to
   anything that is background at that cadence.
4. **Each review emits a five-line Roll-up** written for the review above it.
   The higher review reads only Roll-ups and never reopens the files beneath.
   The 90 seconds this costs is paid when the week is fresh in mind, which makes
   it both cheaper and *more accurate* than reconstructing a month from four
   documents. `03` says reviews "gather evidence from the reviews immediately
   beneath them" — it never said re-read them in full.

Observation **fields** are untouched — all five of `03`'s questions remain. Only
their length is bounded: paragraphs weekly, one line each monthly and quarterly.

**Recheck:** if a field is reliably blank at monthly level, ReviewObservation
needs cadence-specific field sets in v1 — which `03` does not model. Capture it
in the weekly System notes.

**This is the single most important finding for v1.** If the app's review screen
lists every Project and Commitment with a text box under each, it will be
unusable for exactly this reason, and it will look correct in the spec right up
until someone with 21 Commitments opens it.

---

## What this run is testing

Each of these is an Open Question in `design-docs/03-domain-model-specifications.md`
that a quarter of real use will answer. **Do not carry this list into the daily
log** — a daily template with research fields in it is not calm, and Principle 6
outranks data collection. The WeeklyReview template has one section for it
("System notes"), and that is the only place it is captured.

| Question | Source | What to watch |
|---|---|---|
| Is Signal 3–5 hard, or descriptive? | § Signal | How many you actually declare on good and bad days |
| Does the push-to-tomorrow mechanic survive? | § Signal | How often you push; whether the 2-push cap ever bites |
| Does Task need a "Carried Over" or "Missed" state? | § Task | What you actually do with unfinished scheduled Tasks |
| Can a ScheduleItem be "missed" independently of its target? | § ScheduleItem | How often you complete something outside its block |
| Is a MorningLog really a frozen snapshot? | § MorningLog | How often you want to edit it and why |
| What shape is a Metric — target, current value, or series? | § Metric | What your FocusPoints actually need to be judged |
| Are Prompts user-authored, fixed, or both? | § Prompt | Whether you write new ones or reuse |
| Does Dependency need to be a first-class object? | § Outcome | Whether any block needs a "why" recorded |
| What does a Week Score mean? | `notes.md` | Whether you ever want a number at all |

---

## Getting started

[Founding Session](templates/00-founding-session.md).
