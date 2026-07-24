# Daily Flow

## Morning

User wakes up
...
User wants to plan their day.
User opens app.

The app detects if the user has entered a morning entry for today.
If they have an entry, that entry is displayed to them.
If they do not have an entry, they are automatically entered into
the morning entry workflow.

### Morning Entry Workflow

> **Note:**
> Users are provided an option to skip the rest of the entry in page 1.
> The option is provided for days where the user is in a rush
> or is taking an intentional rest day.

#### Page 1 (Greeting)

```
Morning greeting message

How are you feeling?
(Select from range of emotions)

Last night's bed time:
Today's wake up time:

Skip to farewell?
```

#### Page 2 (Priorities Setting)

```
List goals of the week.

Yesterday's outstanding priorities:

Today's 3 priorities:

Potential obstacles & responses:
```

#### Page 3 (Review Agenda)

```
Set time blocks on calendar for the the day's 3 priorities
```

#### Page 3 (Morning Questions)

```
List user entered questions.
Recieve input and save in database.
```


#### Page 4 (Farewell)

```
Morning farewell messsage

List today's 3 priorities (if set).
List goals of the week.
```

### View Morning Entry

## Evening

It is after 6pm.
...
User wants to reflect on their day.
User opens the app.

The app detects if the user has entered an evening entry for today.
If they have an entry, that entry is displayed to them.
If they do not have an entry, they are automatically entered into
the evening entry workflow.


### Evening Entry Workflow


> **Note:** Unlike morning entries, there is no short evening entry workflow.

#### Page 1 (Greeting)

```
Evening greeting message

How are you feeling?
(Select from range of emotions)
```

#### Page 2 (Habits)

```
Display user entered habits on habits tracker with 7 days progress
```


#### Page 3 (Evening Questions)

```
List user entered reminders.

List user entered questions.
Recieve input and save in database.
```

#### Page 4 (Farewell)

```
Evening farewell messsage
```
