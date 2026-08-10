# Ubiquitous Languge

This file contains the different terms used throughout the OLOS environent and
serves as the single point of truth for what each term means.

## Template

**Definition**

**Distinction**

**Rules**

**Relationships**

## Visions Domain

The Visions Domain answers the question
"*What am I trying to accomplish and what am I doing about it?*"

The Visions Domain is the area of the OLOS app designed to help users define a
large goal (a Vision) and break it down into actionable steps.

### Vision

**Definition**

A Vision answers the question of "*Where am I going?*"

A Vision is a large goal the user wants to achieve. They define the direction
that the user wants to take their life in.

**Distinction**

**Rules**

**Relationships**

- Visions create and own Outcomes.

### Outcome

**Definition**

An Outcome answers the question of "*What needs to happen?*"

An Outcome is a real-world accomplishment that takes the user one step closer to
their Vision.

**Distinction**

**Rules**

**Relationships**

- Outcomes may have Dependencies.

#### Outcome Dependency

**Definition**

An Outcome Dependency answers the question of "*What needs to happen before I can do ___?*"

An Outcome may depend on another Outcome being completed before meaningful progress can be
made. Dependencies are a classification of an Outcome-to-Outcome relationship.

**Distinction**

**Rules**

**Relationships**

### Operation

**Definition**

An Operation answers the question of "*What am continuously I responsible for?*"

An Operation is an ongoing area of responsibility. Operations serve to organize
related Tasks, Projects and Commitments with a common purpose. 

**Distinction**

Operations are theoretically infinite.

**Rules**

**Relationships**

- Operations can support Outcomes.

### Project

**Definition**

A Project answers the question of "*How do I accomplish a big task?*"

A Project is an organized effort to accomplish some goal by a target date.
Projects serve to organize related Tasks with one clear goal. 

**Distinction**

Projects are finite by defintion. 

**Rules**

A Project cannot be created without a target end date.

**Relationships**

- Projects create and own Tasks.
- Projects can support Operations and Outcomes.

### Commitment

**Definition**

A Commitment answers the question of "*What repeated behaviors am I promising to do?*"

A Commitment is a repeated behavior that the user has commited to doing.

**Distinction**

**Rules**

**Relationships**

- Commitments can create and own repeated Tasks.
- Commitments can support Projects, Operations and Outcomes.

### Task

**Definition**

A Task answers the question of "*What is my next step?*"

A Task is an action. Tasks serve to inform the user of the next steps they can
take towards some greater goal.

**Distinction**

**Rules**

- Tasks cannot exist without their parent.
- Tasks cannot be ReviewObservation targets.

**Relationships**

## Entry Domain

The Entry Domain answers the question "*What is happening in my life?*"

The Entries Domain is the area of the OLOS environment designed to support
users through reflection and intention setting.

### Entry

**Definition**

An Entry is a recorded interaction with OLOS through which the user documents, prepares
for, or reflects upon their life during a defined period of time.

**Distinction**

**Rules**

**Relationships**
- review Signal

#### Log

**Definition**

A Log answers the question "*What is happening today?*"

A Log describes a user's daily entries. Logs are designed to support a user's
day-to-day life.

**Distinction**

**Rules**

**Relationships**

##### MorningLog (Prepare for the day)

**Definition**

A MorningLog answers the question "*What does today need to accomplish?*"

A MorningLog describes the user's daily morning entry. A MorningLog prepares users
for the day ahead of them.

**Distinction**

**Rules**

**Relationships**

<!-- TODO: move this to a new doc -->
The user will be prompted to enter a MorningLog every morning. MorningLogs serve
to prepare the user for the day. Users are prompted to declare their sleep time
(SleepRecord), how they feel (Mood), priorities for the day (Signal), and
potential Obstacles and Responses they will face today (ObstacleAndResponse).

MorningLogs will remind users of their active Focuses (Weekly, Monthly and Quaterly)
and their scheduled Commitments and Tasks for the day. When entering a MorningLog,
users will be prompted to make time in their agenda for Tasks, Commitments and Signal, providing time estimates for each.

###### Agenda

**Definition**

An agenda is the user's timeline of scheduled events/activites for a given day.

###### Signal

**Definition**

Signal answers the question "*What is a priority today?*"

The concept of Signal comes from the following source:
[Kevin O'Leary talking about working with Steve Jobs on The Diary of a CEO podcast](https://www.youtube.com/watch?v=mpAZehPviLQ&t=535s).

In short, Signal is the 3-5 things that need to get done before you go to bed.
Anything that distracts you from these things are *noise*.

**Rules**
Each MorningLog must declare at least one Signal item.

**Relationships**
- Reviewed by EveningLogs

###### Noise

**Definition**

Noise is anything that distracts the user from their priorities (Signal).

###### Obstacle

**Definition**

An Obstacle answers the question "*What is probable to block me from my priorities today?*"

**Distinction**

An Obstacle is a type of noise.

##### EveningLog (Reflect on the day)

**Definition**

An EveningLog answers the question "*What actually got done today?*"

An EveningLog describes the user's daily evening entry. An EveningLog reflects on what
the user did today.

**Distinction**

**Rules**

**Relationships**

<!-- TODO: move to a seperate doc -->
A user will be prompted to enter an EveningLog every evening. EveningLogs allow
the user to reflect on what they accomplished during the day. Users are prompted
for how the feel (Mood), what they are grateful for today
(GratitudePromptAndResponse), and reflection questions (ReflectionPromptAndResponse).

<!-- TODO: What does it mean to review Signal items? -->
EveningLogs will prompt users to review the date's Signal's, and to mark scheduled
Tasks and Commitments as complete or not.

##### PromptAndResponse

A PromptAndResponse organizes a reusable Prompt with a user entered Response.

###### Prompt

**Definition**

A Prompt answers the question "*What statements do I want to reflect on?*"

A Prompt is a statement that user provides an answer to.

###### Response

**Definition**

A Response is the text entered by the user reflecting on a Prompt.

#### Review

**Definition**

A Review answers the following questions "*What did I do? What did I learn? What needs to change?*"

Reviews serve to reflect on what happened, understand why, identify lessons and
create adjustments as desired. Reviews are how the system continiously re-aligns
with the user's desires.

**Distinction**

A Review describes an Entry different to a Log. Whereas a Log is used to record
daily entries, a Review records an Entry targeting a greater timespan.

**Rules**

**Relationships**

- Reviews create ReviewObservations for each thing Reviewed
- Reviews can create a Focus

<!-- TODO: move to a new doc -->
Reviews serve to prompt the user 
to reflect on user actions in a defined time period (TimePeriod)


###### ReviewObservation

**Definition**

A ReviewObservation targets one specific object to review and asks the questions
"*What happened with this target in this time period? Why? How do I feel about this?  What did I learn? What adjustments do I want to make?*"

ReviewObservations hold a user's review for a specific target. The target can be a
member of the Vision Domain or another member of the Entry Domain.

**Distinction**

**Rules**

**Relationships**



<!-- TODO: these need better names -->
Users are prompted to enter a few sentences reflecting on what happened with the target
(Reflection), what they learned (Lessons), what changes they want to make (Adjustments)
and they can optionally provide a score on the target during the time period (Score).

MorningLogs will remind users of their active Focuses and their scheduled Commitments
and Tasks for the day. When entering a MorningLog, users will be prompted to make
time in their agenda for Tasks, Commitments and Signal, providing time estimates
for each.

##### WeeklyReview (Review Execution)

A WeeklyReview answers the question "*Did I live according to my intentions this week?*"

WeeklyReviews focus on the day-today execution of the user's life.
Users will review daily Logs, Tasks, Commitments, Projects and the WeeklyFocus
of the previous week.

<!-- TODO: what does it mean to review Logs for the week? -->

##### MonthlyReview (Review Progress)

A MonthlyReview answers the question "*Am I actually moving my life forward?*"

MonthlyReviews focus on the user's progress towards their Visions and making
adjustments as needed. Users will review Outcomes, Projects, Operations,
and the MonthlyFocus and WeeklyFocuses of the previous month.

##### QuarterlyReview (Review Direction)

A QuarterlyReview answers the question "*Am I still pursing the right things?*"

QuarterlyReviews focus on the user's direction in life and updating that direction
if necessary. Users will review Visions, Outcomes, Operations, and the QuarterlyFocus
and MonthlyFocuses of the previous quarter.

###### Quarter

A quarter is a duration of 3 months. 4 quarters make up a calendar year.

A quarter is a term and not an object in the Domain Model.

### Focus

A Focus help users answer the question "*What matters right now?*"

A Focus is time-bounded (TimePeriod) and contains FocusPoints of what the user wants
to prioritize during that period of time.

Whereas a Review looks backwards and reflects, a Focus looks forward and directs attention.

When creating a Focus, users will declare 1-3 FocusPoints.

#### FocusPoint

A FocusPoint answers the question "*What deserves my attention?*"

FocusPoints can be qualitative, quantitative, behavioral or relational.
It is up to the user to decide where their attention is should be prioritized.

FocusPoints are ordered by priority and have a Statement and Reasoning.
FocusPoints may contain Metrics.

FocusPoints may support Outcomes, Operations, Projects or Commitments.

##### FocusStatement

A FocusStatement is a declared FocusPoint

##### Metric

A Metric answers the question "*How can I measure my attention?*"

Metrics can optionally be added to FocusPoints. Not all FocusPoints will be measurable.
It is up to the user to determine if Metrics can be added to a FocusPoint.

Metrics provide a way for users to measure if they are actually directing their
attention towards a FocusPoint by providing targets to strive for.

#### WeeklyFocus

A WeeklyFocus answers the question "*What matters the most this week?*"

A WeeklyFocus is created before a week during a WeeklyReview and users are reminded
of this focus in every MorningLog. WeeklyFocuses are then reviewed during the next
WeeklyReview.

#### MonthlyFocus

A MonthlyFocus answers the question "*What deserves sustained attention this month?*"

A MonthlyFocus is created before a month during a MonthlyReview and users are reminded
of this focus in every MorningLog. MonthlyFocuses are then reviewed during the next
MonthlyReview.

MonthlyFocus are reviewed alongside the WeeklyFocuses of the same month.
The WeeklyFocuses serve to inform the user of what happened during the month.

#### QuarterlyFocus

A QuarterlyFocus answers the question "*What season of life am I in?*"

A QuarterlyFocus is created before a quarter during a QuarterlyReview and users are
reminded of this focus in every MorningLog. QuarterlyFocuses are then reviewed during
the next QuarterlyReview.

QuarterlyFocus are reviewed alongside the MonthlyFocuses of the same quarter.
The MonthlyFocuses serve to inform the user of what happened during the quarter.
