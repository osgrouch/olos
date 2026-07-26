# Daily Flow

The following details the daily flow that a user experiences everyday when using this journal app.
The intention of this exercise is to determine the Minimum Viable Product (MVP) for v1.

## Morning

> **Note:**
> The exact time which the app automatically routes users to the morning entry workflow
> will be customizable in the Settings page.

It is morning time.
...
User wants to plan their day.
User opens app.

```
The app detects if the user has entered a morning entry for today.
If they have an entry, they are routed to the homepage.
If they do not have an entry, they are automatically entered into
the morning entry workflow.
```

### Morning Entry Workflow

#### Section 1 (Greeting)

```
Morning greeting message

How are you feeling?
Display range of emotions.
Prompt for short explanation.

Last night's bed time:
Today s wake up time:
```

User enters data.

> **Note:**
> Users are provided an option to skip the rest of the entry.
> This option is provided for days where the user is in a rush
> or is taking an intentional rest day.

#### Section 2 (Priorities Setting)

> **Note:**
> Signal is the 3-5 things that need to get done before you go to bed.
> Anything that distracts you from these things are **noise**.
> [Source: Kevin O'Leary talking about working with Steve Jobs on The Diary of a CEO podcast.](https://www.youtube.com/watch?v=mpAZehPviLQ&t=535s)

```
Display the defintion of the signal-to-noise ratio concept.

List goals of the week at top of page, if any exist.

Prompt for "Signal" (Mandatory | min 3, max 5)

Display any Signal items marked as "Push to Tomorrow" from yesterday evening.
Prompt user to add Signal item to today's list or mark as "Won't Do"

Prompt for "Potential Obstacles & Expected Responses" (Mandatory | min 3, max 5)
```

User enters data.

#### Section 3 (Review Agenda)

> **Note:**
> I envision this page to one day work with Apple's API to display the user's
> Apple Calendar and Reminders directly in the app.
> This feature is not a part of the MVP for v1.

```
Display entered signal list.
Display user entered habits and record of this week.

Display 2min timer.
Do not allow user to continue until timer is at 0.
```

> **Note:**
> Timer should be modifable in the Settings page.

User creates time blocks in their day to dedicate towards declared priorities.
User reviews the day's reminders and enters more.

#### Section 3 (Morning Questions)

> **Note:**
> The questions displayed on this screen will be those the user set.
> It is possible for no questions to be set.
> If that is the case, this page will only prompt the user for new questions.

```
List user entered questions and receive input, if any exist
Allow user to enter a new question and save it (Optional)
```

User enters data.

#### Section 4 (Farewell)

```
Morning farewell messsage
```

User presses "End" button and is routed to the homepage.

## Evening

> **Note:**
> The exact time which the app automatically routes users to the evening entry workflow
> will be customizable in the Settings page.

It is evening time.
...
User wants to reflect on their day.
User opens the app.

```
The app detects if the user has entered an evening entry for today.
If they have an entry, the are routed to the homepage.
If they do not have an entry, they are automatically entered into
the evening entry workflow.
```

### Evening Entry Workflow


> **Note:**
> Unlike morning entries, there is no short evening entry workflow.

#### Section 1 (Greeting)

```
Evening greeting message

How are you feeling?
Display range of emotions
```
User enters selects an emotion

#### Section 2 (Signal Review)

> **Note:**
> If the user skipped the morning entry, then this page will be skipped automatically.

```
Display Signal list from morning entry.
Prompt user to select an option for each Signal item:
Options are "Complete", "Push to Tomorrow" or "Won't Do"

Display Obstacles & Responses from morning entry.
```

User enters data.

#### Section 2 (Habits & Evening Questions)

> **Note:**
> Any habits that have already been marked as complete can be changed to "Won't Do" from this page.

```
List Habits, if any exist.
Provide "Mark as Complete" and "Won't Do" options (Mandatory on existing habits)

List user entered questions and receive input, if any exist
Allow user to enter a new question and save it (Optional)
```

User enters data.

#### Section 4 (Farewell)

```
Evening farewell messsage
```

User presses "End" button and is routed to the homepage.
