# Ubiquitous Languge

This file contains the different terms used throughout the OLOS environent and
serves as the single point of truth for what each term means.

## Visions Domain

The Visions Domain answers the question
"*What am I trying to accomplish and what am I doing about it?*"

The Visions Domain is the area of the OLOS app designed to help users define a
large goal (a Vision) and break it down into actionable steps.

### Vision

A Vision answers the question of "*Where am I going?*"

A Vision is a large goal the user wants to achieve. They define the direction
that the user wants to take their life in.

Visions create and own Outcomes.

### Outcome

An Outcome answers the question of "*What needs to happen?*"

An Outcome is a real-world accomplishment that takes the user one step closer to
their Vision.

#### Outcome Dependency

An Outcome Dependency answers the question of "*What needs to happen before I can do ___?*"

An Outcome may depend on another Outcome being completed before meaningful progress can be
made. Dependencies are not formal objects but a classification of an Outcome-to-Outcome
relationship.

### Operation

An Operation answers the question of "*What am continuously I responsible for?*"

An Operation is an ongoing area of responsibility. Operations serve to organize
related Tasks, Projects and Commitments with a common purpose. Operations are
theoretically infinite.

Operations can support Outcomes.

### Project

A Project answers the question of "*How do I accomplish a big task?*"

A Project is an organized effort to accomplish some goal by a target date.
Projects serve to organize related Tasks with one clear goal. Projects are
finite by defintion. A Project cannot be created without a target end date.

Projects can support Operations and Outcomes.

### Commitment

A Commitment answers the question of "*What repeated behaviors am I promising to do?*"

A Commitment is a repeated behavior that the user has commited to doing.
Commitments can create repeated Tasks.

Commitments can support Projects, Operations and Outcomes.

### Task

A Task answers the question of "*What is my next step?*"

A Task is an action. Tasks serve to inform the user of the next steps they can
take towards some greater goal. Tasks cannot exist without their parent.

## Entry Domain

The Entry Domain answers the question "*What is happening in my life?*"

The Entries Domain is the area of the OLOS environment designed to support
users through reflection and intention setting.

### Entry

An Entry defines the shared behavior of Log and Review types. It is an abstract
parent which both Log and Review inherit and extend.

#### Log

A Log answers the question "*What is happening today?*"

A Log describes a user's daily entries. Logs are designed to support a user's
day-to-day life.

A Log defines the shared behavior of MorningLog and EveningLog. It is an abstract
parent which both MorningLog and EveningLog inherit and extend.

##### MorningLog (Prepare for the day)

A MorningLog answers the question "*What does today need to accomplish?*"

The user will be prompted to enter a MorningLog every morning. MorningLogs serve
to prepare the user for the day. Users are prompted to declare their sleep time
(SleepRecord), how they feel (Mood), priorities for the day (Signal), and
potential Obstacles and Responses they will face today (ObstacleAndResponse).

MorningLogs will remind users of their active Focuses (Weekly, Monthly and Quaterly)
and their scheduled Commitments and Tasks for the day. When entering a MorningLog,
users will be prompted to make time in their agenda for Tasks, Commitments and Signal, providing time estimates for each.

###### Agenda

An agenda is the user's timeline of scheduled events/activites for a given day.

An agenda is a term and not a domain model object.

###### Signal

A Signal answers the question "*What is a priority today?*"

Users must declare at least one Signal.

> **Note:**
> The concept of Signal comes from the following
> [Source: Kevin O'Leary talking about working with Steve Jobs on The Diary of a CEO podcast.](https://www.youtube.com/watch?v=mpAZehPviLQ&t=535s)
> In summary:
> Signal is the 3-5 things that need to get done before you go to bed.
> Anything that distracts you from these things are *noise*.

###### Noise

Noise is anything that distracts the user from their declared Signal items.

Noise is not a domain model object, but rather a term that encompasses anything that
is not a priority today.

###### Obstacle

An Obstacle answers the question "*What is probable to block me from my priorities today?*"

An Obstacle is a type of noise. Users must declare at least one Obstacle.

##### EveningLog (Reflect on the day)

A EveningLog answers the question "*What actually got done today?*"

A user will be prompted to enter an EveningLog every evening. EveningLogs allow
the user to reflect on what they accomplished during the day. Users are prompted
for how the feel (Mood), what they are grateful for today
(GratitudePromptAndResponse), and reflection questions (ReflectionPromptAndResponse).

<!-- TODO: What does it mean to review Signal items? -->
EveningLogs will prompt users to review the date's Signal's, and to mark scheduled
Tasks and Commitments as complete or not.

##### PromptAndResponse Types

A PromptAndResponse organizes a reusable Prompt with a user entered Response.

###### Prompt

A Prompt answers the question "*What statements do I want to reflect on?*"

A Prompt is a statement that user provides an answer to.

Concrete types are:
- GratitudePrompt
- ReflectionPrompt

###### Response

A Response is the text entered by the user reflecting on a Prompt.

#### Review

A Review answers the following questions "*What did I do? What did I learn? What needs to change?*"

A Review describes an Entry different to a Log. Reviews serve to prompt the user 
to reflect on user actions in a defined time period (TimePeriod), understand why they
happened the way they did, and to identify adjustments in the user's life so they
can continue to make progress towards their Visions.

Reviews create ReviewObservations, each targeting an individual object from the
Vision Domain or a previous Focus.

The Reviews derive adjustments for the future in the form of a Focus.

###### ReviewObservation

A ReviewObservation targets one specific object to review and asks the questions
"*What happened with this target in this time period? Why? How do I feel about this?  What did I learn? What adjustments do I want to make?*"

The user will be prompted to create ReviewObservations during each Review, focusing
on specific objects to Review. What objects exactly are dictated by the different
Review types below.

<!-- TODO: these need better names -->
Users are prompted to enter a few sentences reflecting on what happened with the target
(Reflection), what they learned (Lessons), what changes they want to make (Adjustments)
and they can optionally provide a score on the target during the time period (Score).

MorningLogs will remind users of their active Focuses and their scheduled Commitments
and Tasks for the day. When entering a MorningLog, users will be prompted to make
time in their agenda for Tasks, Commitments and Signal, providing time estimates
for each.

####### Targeting Vision
####### Targeting Outcome
####### Targeting Operation
####### Targeting Project
####### Targeting Commitment
####### Targeting Task
####### Targeting Focus

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
