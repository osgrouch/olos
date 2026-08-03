# Glossary

## Check In

**Check Ins** - When the user first enters a morning or evening entry,
they will be prompted for their mood. Morning entries will also prompt for
bed time and wake up time.

### How is it used?

### What information does it have?

### How does this serve the purpose of the app?

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
id: integer
creation_date: timestamp
text: string
complete: boolean
pushed_count: integer, max 2
```

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
date: timestamp
text: string
linked_response: integer referencing response
linked_note: integer referencing obstacle_note, may be null

RESPONSE
id: integer
date: timestamp
text: string
linked_obstacle: integer referencing obstacle, not null

OBSTACLE_NOTE
id: integer
date: timestamp
text: string
linked_obstacle: integer referencing obstacle, not null
```

### How does this serve the purpose of the app?

## Habit

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
id: integer
title_text: string, max 100 characters
why_text: string, max 8000 characters
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
active: boolean
time: day | evening
text: string, max 100 characters

QUESTION_RESPONSE
id: integer
linked_question: integer referencing question
date: timestamp
text: string, max 8000 characters
```

### How does this serve the purpose of the app?
