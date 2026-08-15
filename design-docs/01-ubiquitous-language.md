# Ubiquitous Language

This file contains the different terms used throughout the OLOS environment and
serves as the single point of truth for what each term means.

## Template

**Definition**

**Distinction**

**Rules**

**Relationships**

## Vision Domain

The Vision Domain answers the question
"*What am I trying to accomplish and what am I doing about it?*"

The Vision Domain is the area of the OLOS app designed to help users define a
large goal (a Vision) and break it down into actionable steps.

### Vision

**Definition**

A Vision answers the question of "*Where am I going?*"

A Vision is a large goal the user wants to achieve. They define the direction
that the user wants to take their life in.

**Relationships**

- Visions create and own Outcomes.

### Outcome

**Definition**

An Outcome answers the question of "*What needs to happen?*"

An Outcome is a real-world accomplishment that advances the user towards a Vision.

**Rules**

- Outcomes own nothing

**Relationships**

- may have Dependencies
- are created and owned a Vision
- may be supported by Operations, Projects and Commitments

#### Dependency

**Definition**

A Dependency answers the question of "*What needs to happen before I can do ___?*"

A Dependency defines a type of relationship from one Outcome to another Outcome.
An Outcome marked as a Dependency blocks significant progress being made on another
Outcome until the Outcome marked as Dependency is completed. This provides a way for
users to create a path towards achieving a Vision.

### Operation

**Definition**

An Operation answers the question of "*What am I continuously responsible for?*"

An Operation is an ongoing area of responsibility. Operations serve to organize
related Projects, Commitments and Tasks with a common purpose.

**Distinction**

Operations are theoretically infinite.

**Rules**

- Operations do not have end dates

**Relationships**

- may create and own Projects, Commitments and Tasks
- may support Outcomes

### Project

**Definition**

A Project answers the question of "*How do I accomplish a big task?*"

A Project is an organized effort to accomplish some goal by a target date.
Projects serve to organize related Tasks with one clear goal.

**Distinction**

Projects are finite by definition.

**Rules**

- A Project cannot be created without a target end date.
- A Project may continue beyond its original target end date.
- Project end dates are modifiable.

**Relationships**

- may create and own Tasks
- may be created and owned by Operations
- may support Outcomes
- may be supported by Commitments

### Commitment

**Definition**

A Commitment answers the question of "*What repeated behaviors am I promising to do?*"

A Commitment is a repeated behavior that the user has committed to doing.

**Distinction**

**Rules**

**Relationships**

- may create and own repeated Tasks
- may support Projects and Outcomes

### Task

**Definition**

A Task answers the question of "*What is my next step?*"

A Task is an action. Tasks serve to inform the user of the next steps they can
take towards some greater goal.

**Rules**

- own nothing
- cannot exist without a parent
- cannot be ReviewObservation targets

**Relationships**

- are created and owned by a singular Operation, Project or Commitment

## Entry Domain

The Entry Domain answers the question "*What is happening in my life?*"

The Entry Domain is the area of the OLOS environment designed to support
users through reflection and intention setting.

### Entry

**Definition**

An Entry is a recorded interaction with OLOS through which the user documents, prepares
for, or reflects upon their life during a defined period of time.

### Log

**Definition**

A Log answers the question "*What is happening today?*"

A Log describes a user's daily entries. Logs are designed to support a user's
day-to-day life.

### MorningLog (Prepare for the day)

**Definition**

A MorningLog answers the question "*What does today need to accomplish?*"

A MorningLog describes the user's daily morning entry. A MorningLog prepares users
for the day ahead of them by helping them setup their day's agenda.

**Relationships**

- creates and owns SleepRecord
- creates and owns Mood
- references active Focuses (Weekly, Monthly and Quarterly)
- references today's schedule Tasks and Commitments
- creates and owns Signal
- creates and owns ObstacleAndResponse

#### Agenda

**Definition**

An agenda is the user's timeline of scheduled events/activities for a given day.

#### SleepRecord

**Definition**

A SleepRecord records the user's bedtime and wakeup time.

**Relationships**

- is created and owned by a MorningLog

#### Mood

**Definition**

Mood records the user's mood in a Log.

**Relationships**

- is created and owned by a Log (MorningLog or EveningLog)

#### Signal

**Definition**

Signal answers the question "*What is a priority today?*"

The concept of Signal comes from the following source:
[Kevin O'Leary talking about working with Steve Jobs on The Diary of a CEO podcast](https://www.youtube.com/watch?v=mpAZehPviLQ&t=535s).

In short, Signal is the 3-5 things that need to get done before you go to bed.
Anything that distracts you from these things are *noise*.

**Rules**

- each MorningLog must declare at least one Signal item

**Relationships**

- may be reviewed by an EveningLog

#### Noise

**Definition**

Noise is anything that distracts the user from their priorities (Signal).

#### ObstacleAndResponse

**Definition**

An ObstacleAndResponse organizes an Obstacle and a Response.

**Relationships**

- is created and owned by a MorningLog
- may create an Obstacle
- references Obstacle
- creates and owns Response

##### Obstacle

**Definition**

An Obstacle answers the question "*What is probable to block me from my priorities today?*"

An Obstacle is any significant blocker to the day's Signal items, identified by the user.

**Distinction**

An Obstacle is a type of noise.

**Relationships**

- may be referenced by any number of ObstacleAndResponse

##### Response

**Definition**

A Response is the text entered by the user reflecting on some prompt.

**Relationships**

- created and owned be some AndResponse

### EveningLog (Reflect on the day)

**Definition**

An EveningLog answers the question "*What actually got done today?*"

An EveningLog describes the user's daily evening entry. An EveningLog reflects on what
the user did today.

**Distinction**

**Rules**

**Relationships**

- creates and owns Mood
- creates and owns GratitudePromptAndResponse
- creates and owns ReflectionPromptAndResponse
- references active Focuses (Weekly, Monthly and Quarterly)
- creates and owns SignalReview
  <!-- TODO: Should these be a formal Review object too? -->
- references today's schedule Tasks and Commitments

#### PromptAndResponse

A PromptAndResponse organizes a reusable Prompt with a user entered Response.

##### Prompt

**Definition**

A Prompt answers the question "*What statements do I want to reflect on?*"

A Prompt is a statement that user provides an answer to in the form of a Response.

## Review And Focus Domain

The Review And Focus Domain answers the questions
"*What did I learn from my experience? What do I want to change moving forward?*"

The Review And Focus Domain supports users by encouraging accountability through
reflection and growth through intention-setting for an upcoming time period.

### Review

**Definition**

A Review answers the following questions "*What did I do? What did I learn? What needs to change?*"

Reviews serve to reflect on what happened, understand why, identify lessons and
create adjustments as desired. Reviews are how the system continuously re-aligns
with the user's desires.

Reviews gather evidence from the reviews immediately beneath them in the temporal
hierarchy (QuarterlyReview -> MonthlyReview -> WeeklyReview). Each review synthesizes
the period below it into observations, patterns, and a direction for the next period
in the form of a Focus.

**Distinction**

A Review describes an Entry different to a Log. Whereas a Log is used to record
daily entries, a Review records an Entry targeting a greater timespan.

**Rules**

**Relationships**

- gather evidence from other Reviews in the time period being evaluated
- create ReviewObservations for each thing reviewed
- creates a Focus

#### ReviewObservation

**Definition**

A ReviewObservation targets one specific object to review and asks the questions
"*What happened with this target in this time period? Why? How do I feel about this?  What did I learn? What adjustments do I want to make?*"

ReviewObservations hold a user's review for a specific target. The target under review
is used as evidence for the user to reflect on what happened and why; then derive
the lessons learned and changes to make moving forward. ReviewObservations are the central
point of Reviews and serve to help the user Foderive FocusPoints.

**Distinction**

**Rules**

- each ReviewObservation reviews only one thing

**Relationships**

- is created and owned by a Review
- may evaluate an individual Vision, Outcome, Operation, Project, Commitment, Signal, Focus

### WeeklyReview (Review Execution)

**Definition**

A WeeklyReview answers the question "*Did I live according to my intentions this week?*"

WeeklyReviews reflect on the day-to-day execution of the user's life in the last
seven days. WeeklyReviews serve as an opportunity for users to examine their week
and highlight priorities for their upcoming week by creating a WeeklyFocus.

WeeklyReviews gather primary evidence from directly reviewing the previous WeeklyFocus,
Projects and Commitments. Secondary evidence is provided by the weeks's Logs and Tasks.
This evidence is used to provide an objective overview of what happened during the week.
The user provides a subject perspective of these events through ReviewObservations.
Through this process, users derive adjustments for the upcoming week in a WeeklyFocus.

**Distinction**

**Rules**

**Relationships**

- creates a WeeklyFocus
- may evaluate Projects and a previous WeeklyFocus
- gathers evidence from Logs, Commitments and Tasks of the week

### MonthlyReview (Review Progress)

**Definition**

A MonthlyReview answers the question "*Am I actually moving my life forward?*"

MonthlyReviews serve to review the progress made towards Outcomes over a month-long period.
MonthlyReviews gather evidence of progress from the WeeklyReviews in the completed month.
MonthlyReviews create a MonthlyFocus which declares the areas of priority for the
upcoming month.

MonthlyReviews gather primary evidence from directly reviewing the previous MonthlyFocus,
Outcomes, Operations and Projects. Secondary evidence is provided by WeeklyReviews
recorded in the month under review. This evidence is used to provide an objective overview
of what happened during the month. The user provides a subject perspective of the month's
events through ReviewObservations. Through this process, users derive adjustments for the upcoming month in a MonthlyFocus.

**Distinction**

**Rules**

**Relationships**

- create MonthlyFocus
- may evaluate Outcomes, Operations, Projects and previous MonthlyFocus
- gathers evidence from WeeklyReviews of the completed month

### QuarterlyReview (Review Direction)

**Definition**

A QuarterlyReview answers the question "*Am I moving towards the right things?*"

QuarterlyReviews reflect the progress made towards Outcomes in the previous quarter
and on the greater Vision(s) behind the Outcomes the user is working towards.
QuarterlyReviews reflect on the direction of the entire system and serve to periodically
question the user on their chosen direction to ensure they are still moving towards
the correct goals.

QuarterlyReviews gather primary evidence from directly reviewing the previous
QuarterlyFocus, Visions, Outcomes and Operations. Secondary evidence is provided by
MonthlyReviews recorded in the quarter under review. This evidence is used to provide
an objective overview of what happened during the quarter. The user provides a subject
perspective of the quarter's events through ReviewObservations. Through this process,
users derive adjustments for the upcoming quarter in a QuarterlyFocus.

**Distinction**

**Rules**

**Relationships**

- create QuarterlyFocus
- may evaluate Visions, Outcomes, Operations and previous QuarterlyFocus
- gathers evidence from the MonthlyReviews of the completed quarter

#### Quarter

**Definition**

A quarter is a duration of 3 months. 4 quarters make up a calendar year.

### Focus

**Definition**

A Focus help users answer the question "*What matters right now?*"

Focus organizes user intentions over a period of time.

**Distinction**

Whereas a Review looks backwards and reflects, a Focus looks forward and directs attention.

**Rules**

- may have more than one FocusPoint

**Relationships**

- create and own FocusPoint

#### FocusPoint

**Definition**

A FocusPoint answers the question "*What deserves my attention?*"

FocusPoints organize a statement of attention with reasoning. They can be qualitative,
quantitative, behavioral or relational. A FocusPoint may contain Metrics: tracked daily
and used to evaluate a FocusPoint in a Review.

**Distinction**

**Rules**

**Relationships**

- may create Metrics
- support Outcomes

#### Metric

**Definition**

A Metric answers the question "*How can I measure my attention?*"

Metrics are an optional measure used to evaluate a FocusPoint.

**Distinction**

**Rules**

- optional

**Relationships**

- created and owned by a FocusPoint

### WeeklyFocus

**Definition**

A WeeklyFocus answers the question "*What matters the most this week?*"

WeeklyFocuses are created with specific points of focus for the upcoming week.
A WeeklyFocus is created before a week during a WeeklyReview and users are reminded
of this focus in every MorningLog of the week. WeeklyFocuses are then reviewed during
the next WeeklyReview.

**Distinction**

**Rules**

**Relationships**

- referenced by MorningLogs
- reviewed by WeeklyReview

### MonthlyFocus

**Definition**

A MonthlyFocus answers the question "*What deserves sustained attention this month?*"

A MonthlyFocus is created before a month during a MonthlyReview and users are reminded
of this focus in every MorningLog. MonthlyFocuses are then reviewed during the next
MonthlyReview.

**Distinction**

**Rules**

**Relationships**

- referenced by MorningLogs
- reviewed by MonthlyReview

### QuarterlyFocus

**Definition**

A QuarterlyFocus answers the question "*What season of life am I in?*"

A QuarterlyFocus is created before a quarter during a QuarterlyReview and users are
reminded of this focus in every MorningLog. QuarterlyFocuses are then reviewed during
the next QuarterlyReview.

**Distinction**

**Rules**

**Relationships**

- referenced by MorningLogs
- reviewed by QuarterlyReview
