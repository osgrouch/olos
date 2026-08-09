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

#### Dependency

A Dependency answers the question of "*What needs to happen before I can do ___?*"

A Dependency is a label placed on an Outcome that blocks another Outcome from
being completed. Dependencies are not formal objects but a classification of
an Outcome.

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

## Entries Domain

The Entries Domain answers the question "*What is happening in my life?*"

The Entries Domain is the area of the OLOS environment designed to support
users through frequent reflection.

### Entry Type

An Entry defines the shared behavior of Log and Review types.

#### Log Type

A Log answers the question "*What is happening today?*"

A Log describes a user's daily entries. Logs are designed to support a user's
day-to-day life.

##### MorningLog (Prepare for the day)

A MorningLog answers the question "*What does today need to accomplish?*"

The user will be prompted to enter a MorningLog every morning. MorningLogs serve
to prepare the user for the day. Users are prompted to declare their sleep time
(SleepRecord), how they feel (Mood), priorities for the day (Signal), and
potential Obstacles and Responses they will face today (ObstacleAndResponse).

MorningLogs will remind users of their WeeklyFocus and their scheduled Commitments
and Tasks for the day. When entering a MorningLog, users will be prompted to make
time in their agenda for Tasks, Commitments and Signal, providing time estimates
for each.

###### Agenda

An agenda is the user's timeline of scheduled events/activites for a given day.

###### Obstacle

An Obstacle answers the question "*What is probable to block me from my priorities today?*"

Users must declare at least one Obstacle.

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

###### Prompt Type

A Prompt answers the question "*What statements do I want to reflect on?*"

A Prompt is a statement that user provides an answer to.

Concrete types are:
- GratitudePrompt
- ObstaclePrompt

###### Response

A Response is the text entered by the user reflecting on a Prompt.

#### Review Type

A review answers the following questions "*What did I do? What did I learn? What needs to change?*"

A Review describes an Entry different to a Log. Reviews serve to prompt the user 
to reflect on a completed time period greater than a day.

The purpose of a Review is to reflect, learn and derive adjustments for the future
in the form of a Focus.

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

### Focus

A Focus help users answer the question "*What deserves my attention?*"

A Focus is a statement of what the user wants to prioritize during a defined
period of time. It is not intended to be a goal, but instead a direction for the
user's attention during the set timeframe.

Wheras a Review looks backwards and reflects, a Focus looks forward and directs attention.

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

#### QuarterlyFocus

A QuarterlyFocus answers the question "*What season of life am I in?*"

A QuarterlyFocus is created before a quarter during a QuarterlyReview and users are
reminded of this focus in every MorningLog. QuarterlyFocuses are then reviewed during
the next QuarterlyReview.

