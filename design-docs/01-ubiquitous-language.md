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

- Outcomes own nothing

**Relationships**

- Outcomes may have Dependencies.

#### Outcome Dependency

**Definition**

An Outcome Dependency answers the question of "*What needs to happen before I can do ___?*"

An Outcome may depend on another Outcome being completed before meaningful progress can be
made. Dependencies are a classification of an Outcome-to-Outcome relationship.

**Distinction**

**Rules**

- Outcomes can only have other Outcomes as Dependencies

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

- Operations create and own Tasks.
- Operations can support Outcomes.

### Project

**Definition**

A Project answers the question of "*How do I accomplish a big task?*"

A Project is an organized effort to accomplish some goal by a target date.
Projects serve to organize related Tasks with one clear goal. 

**Distinction**

Projects are finite by defintion. 

**Rules**

- A Project cannot be created without a target end date.

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

- Tasks are owned by a singular Operation, Project or Commitment.

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
for the day ahead of them by helping them setup their day's agenda.

**Distinction**

**Rules**

**Relationships**

- creates and owns SleepRecord
- creates and owns Mood
- references active Focuses (Weekly, Monthly and Quarterly)
- references today's schedule Tasks and Commitments
- creates and owns Signal
- creates and owns ObstacleAndResponse

###### Agenda

**Definition**

An agenda is the user's timeline of scheduled events/activites for a given day.

###### SleepRecord

**Definition**

A SleepRecord records the user's bedtime and wakeup time.

**Relationships**

- is created and owned by a MorningLog

###### Mood

**Definition**

Mood records the user's mood in a Log.

**Relationships**

- is created and owned by a Log (MorningLog or EveningLog)

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

###### ObstacleAndResponse

**Definition**

An ObstacleAndResponse organizes an Obstacle and a Response.

**Relationships**

- is created and owned by a MorningLog
- can create an Obstacle
- references Obstacle
- creates and owns Response

###### Obstacle

**Definition**

An Obstacle answers the question "*What is probable to block me from my priorities today?*"

An Obstacle is any significant blocker to the day's Signal items, identified by the user.

**Distinction**

An Obstacle is a type of noise.

**Relationships**

- may be referenced by ObstacleAndResponses

###### Response

**Definition**

A Response is the text entered by the user reflecting on some prompt.

**Relationships**

- created and owned be some AndResponse

##### EveningLog (Reflect on the day)

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

##### PromptAndResponse

A PromptAndResponse organizes a reusable Prompt with a user entered Response.

###### Prompt

**Definition**

A Prompt answers the question "*What statements do I want to reflect on?*"

A Prompt is a statement that user provides an answer to in the form of a Response.

## Review And Focus Domain

The Review And Focus Domain answers the questions
"*What did I learn from my experience? What do I want to change moving forward?*"

The Review And Focus Domain supports users by encouraging accoutability through
reflection and growth through intention-setting for an upcoming time period.

### Review

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

##### ReviewObservation

**Definition**

A ReviewObservation targets one specific object to review and asks the questions
"*What happened with this target in this time period? Why? How do I feel about this?  What did I learn? What adjustments do I want to make?*"

ReviewObservations hold a user's review for a specific target. The target can be a
member of the Vision Domain or another member of the Entry Domain.

**Distinction**

**Rules**

**Relationships**
- references Vision and Entry Domain objects 

#### WeeklyReview (Review Execution)

**Definition**

A WeeklyReview answers the question "*Did I live according to my intentions this week?*"

WeeklyReviews reflect on the day-to-day execution of the user's life in the last
seven days. WeeklyReviews serve as an opportunity for users to examine their week
and take accountability. WeeklyFocuses are created with specific points of focus
for the upcoming week.

**Distinction**

**Rules**

**Relationships**
- creates WeeklyFocus
- references Logs, Projects, Commitments, Tasks, and WeeklyFocus

#### MonthlyReview (Review Progress)

**Definition**

A MonthlyReview answers the question "*Am I actually moving my life forward?*"

MonthlyReviews serve to review the progress made towards Outcomes in a month-long period.
MonthlyReviews create a MonthlyFocus which declared the areas of priority for the
upcoming month.

**Distinction**

**Rules**

**Relationships**
- create MonthlyFocus
- references Outcomes, Operations, Projects and MonthlyFocus

#### QuarterlyReview (Review Direction)

**Definition**

A QuarterlyReview answers the question "*Am I moving towards the right things?*"

QuarterlyReviews reflect the progress made in the previous quarter and on the greater
Vision behind the Outcomes the user is working towards. QuarterlyReviews reflect on the
direction of the entire system and serve to periodically re-align the system with the user
by providing an opportunity to make direction-level changes.

**Distinction**

**Rules**

**Relationships**
- create QuarterlyFocus
- references Visions, Outcomes, Operations, QuarterlyFocus, MonthlyFocus

##### Quarter

**Definition**

A quarter is a duration of 3 months. 4 quarters make up a calendar year.

### Focus

**Definition**

A Focus help users answer the question "*What matters right now?*"

Focus organizes user intentions over a period of time.

**Distinction**

Whereas a Review looks backwards and reflects, a Focus looks forward and directs attention.

**Rules**
- Focus can have 1-3 FocusPoint

**Relationships**
- create and own FocusPoint

##### FocusPoint

**Definition**

A FocusPoint answers the question "*What deserves my attention?*"

FocusPoints organize a statement of attention with reasoning. They can be qualitative,
quantitative, behavioral or relational. If a FocusPoint is measurable, objectives
can be declared with Metrics.

**Distinction**

**Rules**

**Relationships**
- can create Metrics
- support Outcomes, Operations, Projects or Commitments

##### Metric

**Definition**

A Metric answers the question "*How can I measure my attention?*"

Metrics are a measurable way to track a FocusPoint.

**Distinction**

**Rules**

**Relationships**

#### WeeklyFocus

**Definition**

A WeeklyFocus answers the question "*What matters the most this week?*"

A WeeklyFocus is created before a week during a WeeklyReview and users are reminded
of this focus in every MorningLog. WeeklyFocuses are then reviewed during the next
WeeklyReview.

**Distinction**

**Rules**

**Relationships**
- referenced by MorningLog and MonthlyReview
- reviewed by WeeklyReview

#### MonthlyFocus

**Definition**

A MonthlyFocus answers the question "*What deserves sustained attention this month?*"

A MonthlyFocus is created before a month during a MonthlyReview and users are reminded
of this focus in every MorningLog. MonthlyFocuses are then reviewed during the next
MonthlyReview.

MonthlyFocus are reviewed alongside the WeeklyFocuses of the same month.
The WeeklyFocuses serve to inform the user of what happened during the month.

**Distinction**

**Rules**

**Relationships**
- referenced by QuarterlyReview
- reviewed by MonthlyReview

#### QuarterlyFocus

**Definition**

A QuarterlyFocus answers the question "*What season of life am I in?*"

A QuarterlyFocus is created before a quarter during a QuarterlyReview and users are
reminded of this focus in every MorningLog. QuarterlyFocuses are then reviewed during
the next QuarterlyReview.

QuarterlyFocus are reviewed alongside the MonthlyFocuses of the same quarter.
The MonthlyFocuses serve to inform the user of what happened during the quarter.

**Distinction**

**Rules**

**Relationships**
- reviewed by QuarterlyReview
