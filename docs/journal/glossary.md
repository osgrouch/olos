# Glossary

```
## Template

### How is it used?

### What information does it have?

### How does this serve the purpose of the app?
```

## Entry

An Entry is the parent object defining core behavior of each specialized Entry.

### How is it used?

This parent class has children for the MorningEntry, EveningEntry, and another
abstract parent: ReviewRecord.

### What information does it have?

```
ENTRY
questions_and_responses: Array<Questions>
review_target: 
```

## Signal

**Signal** - The user's declared priorities for the day.

### How is it used?

Every day the user will declare 3-5 signal items.
Every evening, users will have the option to push a signal item to tomorrow,
for a maximum of 2 times.
On the third day a Habit is shown during the Evening,
it can no longer be pushed to tomorrow.

### What information does it have?

```
SIGNAL
id: integer
creation_date: timestamp
last_edit: timestamp
text: string
complete: boolean
days_delayed: integer
```

> **Note:**
> The `days_delayed` should never be allowed to be more than 2.

### How does this serve the purpose of the app?

## Obstacle & Response

**Obstacle** - These are possible distractions that a user declares in every morning entry.

**Response** - These are the user's pre-emptive responses for how they will handle
an obstacle if it arises during the day.

### How is it used?

Every morning, users are prompted to enter potential obstacles they may face
and their expected responses. This is to help the user envision their day and
prepare them for facing frustrations that may arise throughout their day.
Each Obstacle entered must have a Response entered as well.

Every evening, the Obstacle and its linked Response is displayed to the user.
The user can add an Optional note an obstacle.

### What information does it have?

```
OBSTACLE
id: integer
creation_date: timestamp
last_edit: timestamp
text: string
linked_response: Response
linked_note: Obstacle_Note | null

RESPONSE
id: integer
creation_date: timestamp
last_edit: timestamp
text: string
linked_obstacle: Obstacle

OBSTACLE_NOTE
id: integer
creation_date: timestamp
last_edit: timestamp
text: string
linked_obstacle: Obstacle
```

### How does this serve the purpose of the app?

## Habit

<!-- TODO: no longer needed, replace with Commitment object -->

**Habit** - These are behaviors that a user declares.

### How is it used?

Users are shown all currently active habits every evening.
Users can declare a habit as "Complete" everyday.
The Habit will exist as "Incomplete" until it is marked as "Complete".
A user can toggle a habit between two states.
A user is not limited to toggling only today's habits.
They can retroactively mark habits on past dates as complete. 

### What information does it have?

```
HABIT
id: integer
title_text: string
why_text: string
active: boolean
complete: boolean
```

### How does this serve the purpose of the app?


## Questions

**Question** - The user will declare questions to be prompted for everyday.
A question can be categorized as "Day" or "Evening" and will prompt the user
to answer the question during the respective time.

### How is it used?

The user is prompted with questions every morning and evening.
The user must provide an answer to each question promoted.

### What information does it have?

```
QUESTION
id: integer
creation_date: timestamp
last_edit: timestamp
active: boolean
prompt_time_of_day: string
text: string, max 100 characters

QUESTION_RESPONSE
id: integer
linked_question: Question
date: timestamp
text: string
```

> **Note:**
> `Question.prompt_time_of_day` should be either "day" or "evening"

### How does this serve the purpose of the app?

Questions provide opportunities for reflection. They provide
accountability (one of the Product Principles) through reflection.

## Vision

A vision defines a direction that the user has chosen for their life.
They are big goals that this app strives to help the user achieve.

### How is it used?

Users declare Visions during initial account set up, and these visions
are meant to serve as direction in the users life. This app will strive
to help the user achieve their Visions by breaking them down into
practical, actionable steps.

### What information does it have?

```
VISION
id: integer
created_at: timestamp
last_edit: timestamp
retired: boolean
retired_date: timestamp
achieved: boolean
display_order: integer
short_name: string
full_name: string
why_text: string
outcomes: Array<Outcome>
paths: LinkedSet<Outcome>
```

### How does this serve the purpose of the app?

To live intentionally, one must first define their deesired direction.
Visions are this app's way of defining the direction that a user wants
to take their life in. The ultimate goal of this app is to help users
achieve their visions through practical steps.

## Outcome

An outcome is a measurable accomplishment.
They are meant to be completed by the user.

### How is it used?

Visions have a list of associated Outcomes. These outcomes are real-world
accomplishments that would bring the user closer to acheiving their Vision.
Outcomes are made up of Tasks, Projects and Commitments. This is because
different Outcomes will require different work to accomplish them.
Outcomes can block other Outcomes, allowing the user to sequence Outcomes
into a Path of achievable steps. 

### What information does it have?

```
OUTCOME
id: integer
created_at: timestamp
last_edit: timestamp
display_order: integer
completed: boolean
completed_date: timestamp | null
retired: boolean
retired_date: timestamp
display_text: string
target_date: timestamp | null
projects: Array<Project>
commitments: Array<Commitment>
tasks: Array<Task>
```

### How does this serve the purpose of the app?

Outcomes capture practical steps and can be sequenced to create a Path for the
user to follow. This model allows the user to "know what their next steps are,"
one of the Product Principles.

## Path

A Path is an ordered sequence of Outcomes.
It's a concept and not a real object in the app.

## Commitments

Commitments are promises that the user makes about their behavior.
Tasks can optionally be added to commitments.
This can serve as reminders or important steps towards larger commitments.

### How is it used?

### What information does it have?

```
COMMITMENT
id: integer
created_at: timestamp
last_edit: timestamp
display_order: integer
active: boolean
display_text: string
days_of_the_week: Array<integer>
tasks: Array<Task>
```

> **Note:**
> The `days_of_the_week` field is an Array of integers representing the days of the week
> that the user has committed to completing this Commitment.
> The days of the week range from 0 representing Sunday and 6 representing Saturday.

### How does this serve the purpose of the app?

## Project

Projects are organized efforts to complete a large task by a certain date.

### How is it used?

Projects organize multiple Tasks into one organizing body with information
about the group of Tasks. Projects can exist only under Outcomes,
and cannot exist without one.
Projects must be created with an end date. A project is finite and temporary,
and thus must have an end date set.
Projects can be marked as complete when done with an optional reflection,
or they can be abandoned with an optional field for why it was abandoned.

### What information does it have?

```
PROJECT
id: integer
created_at: timestamp
last_edit: timestamp
linked_outcome: Outcome
display_order: integer

title: string
purpose: string
target_end_date: timestamp, not null
on_schedule: boolean
tasks: Array<Task>

completed: boolean
completed_date: timestamp | null
abandoned: boolean
abandonment_date: timestamp | null
```

> **Note:**
> Projects must have a target end date or they are operations not projects

### How does this serve the purpose of the app?

Projects serve to provide organization of Tasks. The mental model of a Project
is an intuitive way to organize Tasks providing a better overall user experience.
This organization helps reduce the complexity of Outcomes and provides further
struture to support the user in achieving their Visions.

## Task

Tasks are actionable steps the user can take.

### How is it used?

Tasks are one of the basic building blocks of the app. Tasks serve to capture
a user's immediate next steps, and are intended to be marked as complete after
real-world action is taken. Tasks can only exist under a parent. Projects,
Commitments, or Outcomes can all have direct Task children. There is no limit to
what can be a Task, and it is up to the discretion of the user to utilize Tasks
effectively.

Tasks are indirectly children of other Projects, Commitments and Outcomes
through this field as well. For example, TaskA whose parent is ProjectA under OutcomeA under VisionA will also be considered a child of OutcomeA and VisionA.

### What information does it have?

```
TASK
id: integer
created_at: timestamp
last_edit: timestamp
for: Project | Commitment | Outcome
display_order: integer
completed: boolean
completed_date: timestamp | null
title: string | null
description: string
target_end_date: timestamp
```

### How does this serve the purpose of the app?

Tasks capture the basic next steps of the user (a Product Principle). Completed
Tasks serve as a historical record of progress and provide evidence of a life
lived intentionally. Tasks can also be added to any of the other elements of the
Vision Hierarchy, which provides a simple way for users to quickly define their
next steps without having to create Outcomes or Projects innecesarily.

## Agenda

An agenda is the user's scheduled events for the day.
It is a concept and not a real object in the project.
I envision this to one day exist as an Apple Calendar integrating fr
in-app support of scheduling Tasks.
