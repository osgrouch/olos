# Founding Session

> One time only. About 90 minutes. This is the substitute for a QuarterlyReview
> you have no data to run — it produces the Visions, Outcomes, Operations, and
> first QuarterlyFocus that every daily log afterwards points back at.
>
> Work in `system/`. Write badly and fast; the first QuarterlyReview will fix it.
> Nothing here is permanent, and an empty system is worse than a rough one.

---

## Order of work, and why

The domain model says direction precedes action — `03` makes Vision→Outcome
mandatory, "an orphaned Outcome has no strategic context." So Outcomes cannot
come first.

But **Visions cannot come first either, in practice.** Asked cold, "where is my
life going" produces either a platitude or a freeze. Operations are the easy
door: they are *descriptive*, not aspirational. You already have them, you are
already doing them, and naming them costs nothing. Once they are on the page,
the Visions are usually sitting inside them, half-visible.

So: **Operations → Visions → Outcomes → wire them together → find the gap.**

---

## 1. Operations (15 min) → `system/03-operations.md`

*What am I continuously responsible for?*

List the areas of your life with **no finish line**. Not goals. Things that
would still need tending if every goal were achieved tomorrow.

The test: if you can picture the day it is done, it is a Project, not an
Operation. "Get a degree" is a Project. "School" is an Operation.

**Cap yourself at five.** Six Operations is six Reminders lists, and a list you
never open is worse than no list.

For each one:

```markdown
## <Name>

**Responsible for** — one sentence.

**Looks neglected when** — the observable symptom. This is what you check in a
MonthlyReview instead of guessing.

**Supports** — (fill in during step 4)
```

- [ ] Written into `system/03-operations.md`
- [ ] One Reminders list per Operation, inside the `OLOS` group

## 2. Visions (20 min) → `system/01-visions.md`

*Where am I going?*

Read your Operations back. For each, ask: **what is this in service of?**

Not all of them are in service of something — some are just maintenance, and
that is fine. The ones that are point at a Vision.

A Vision is a direction, not a destination with a date. It should still be true
in three years. Two or three is plenty; one is acceptable.

```markdown
## <Title>

**Direction** — a paragraph. Where this goes, and what it looks like when the
direction is being followed. Write it in the present tense.

**Status** — Active

**Why this and not something else** — the honest version. Re-read this when a
QuarterlyReview asks whether it is still the right direction.
```

> If nothing comes: your evening prompts already point at this. *"Where did I act
> like the man I want to be?"* and *"Where did I show confidence instead of
> self-doubt?"* describe a person. Who is that person, and what is he moving
> toward? That is a Vision.

- [ ] Written into `system/01-visions.md`

## 3. Outcomes (25 min) → `system/02-outcomes.md`

*What needs to happen?*

Under each Vision, the real-world accomplishments that advance it. Every Outcome
belongs to exactly one Vision — if you cannot place it, either you are missing a
Vision or the Outcome is not one.

The test from `03`: **if you cannot picture the moment it becomes true, it is
not a well-formed Outcome.** "Launch the app" passes. "Be more productive" does
not.

Three to five per Vision. Some should be far away — an Outcome you can finish
this month is probably a Project.

```markdown
### <Title>

**Vision** — which one
**Status** — Open
**True when** — the specific moment you could point at and say: done.
**Depends on** — other Outcomes that must complete first, or none.
**Supported by** — (fill in during step 4)
```

- [ ] Written into `system/02-outcomes.md`
- [ ] No dependency cycles (`03` § Outcome — dev answer: circular dependencies
      are not allowed). Read the chain back out loud; a cycle makes both ends
      permanently unachievable.

## 4. Wire up support (10 min)

Support is an informational link, both ways — it never changes a status or
completes anything. Its whole job is to make the path visible so that a Tuesday
morning Task feels connected to a three-year direction.

Go back through and fill the blanks:

- On each **Outcome**: which Operations, Projects, and Commitments support it?
- On each **Operation**: which Outcomes does it support?
- In **Reminders**: tag each Project's anchor task and each Commitment with
  `#o-<outcome-slug>`.

## 5. Find the gap (10 min)

This is the most valuable ten minutes of the session.

**Outcomes with nothing supporting them.** You declared it matters and nothing
in your week touches it. Either start a Project or a Commitment for it now, or
mark it Open and accept out loud that it is not moving this quarter. Both are
honest. Silence is not.

| Outcome | Supported by | If nothing: start what, or admit what |
|---|---|---|
| | | |

**Operations supporting nothing.** Maintenance, or drift? Maintenance is fine —
some things you do because they must be done. Drift is an Operation absorbing
real time in service of a direction you no longer hold.

## 6. First QuarterlyFocus (10 min) → `system/04-focus.md`

*What season of life am I in?*

Name the season in one line. Then **two** FocusPoints, maximum.

```markdown
## QuarterlyFocus · YYYY-Qn

**The season** —

### FocusPoint 1
**Statement** —
**Because** —
**Supports** —
**Metric** *(optional)* —
```

- [ ] Banner created on `OLOS Rituals` spanning the rest of the quarter,
      titled `Q · <season>`

## 7. Close

- [ ] `system/` committed and pushed to the private repo
- [ ] Reminders: `OLOS` group, one list per Operation, sections for Projects,
      `#commitment` on every recurring reminder
- [ ] Calendar: `OLOS Rituals` and `OLOS Blocks` exist, anchors imported, times
      corrected to your actual schedule
- [ ] Tonight: first EveningLog
- [ ] Sunday: first WeeklyReview, which produces the first WeeklyFocus

There is no WeeklyFocus until Sunday. That is correct — leave the `W ·` line in
the daily log blank until then rather than inventing one. The system is supposed
to be built by its own reviews.
