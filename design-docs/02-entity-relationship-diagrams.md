# Entity Relationship Diagrams (with Mermaid)

## Vision Domain
``` mermaid
---
config:
  layout: elk
title: Vision Domain Entity Relationship Diagram
---
erDiagram
  direction TB

  Vision ||--o{ Outcome : "creates and owns"

  Outcome }o--o{ Outcome : "depends on"
  Outcome }o--o{ Operation : "may be supported by"
  Outcome }o--o{ Project : "may be supported by"
  Outcome }o--o{ Commitment : "may be supported by"

  Operation |o--o{ Commitment : "may create and own"
  Operation |o--o{ Project : "may create and own"
  Operation |o--o{ Task : "may create and own"

  Project }o--o{ Commitment : "may be supported by"
  Project |o--o{ Task : "may create and own"

  Commitment |o--o{ Task : "may create and own repeated"
```

## Entry Domain

``` mermaid
---
title: Entry Inheritance Types
---
classDiagram
    direction LR

    class Entry {
        <<abstract>>
    }

    class Log {
        <<abstract>>
    }

    class Review {
        <<abstract>>
    }

    class MorningLog
    class EveningLog

    class WeeklyReview
    class MonthlyReview
    class QuarterlyReview

    Entry <|-- Log
    Entry <|-- Review

    Log <|-- MorningLog
    Log <|-- EveningLog

    Review <|-- WeeklyReview
    Review <|-- MonthlyReview
    Review <|-- QuarterlyReview
```

### MorningLog

``` mermaid
---
title: MorningLog Entity Relationship Diagram
---
erDiagram
  direction TB

  MorningLog ||--|| SleepRecord: "creates and owns"
  MorningLog }o--o{ Focus : "references active"
  MorningLog }o--o{ Commitment : "references today's scheduled"
  MorningLog }o--o{ Task : "references today's scheduled"
  MorningLog ||--|{ Signal : "creates and owns"
  MorningLog ||--|{ ObstacleAndResponse : "creates and owns"
  MorningLog ||--o{ ScheduleItem : "creates"

  Commitment |o--|| ScheduleItem : "is scheduled by"
  Task |o--|| ScheduleItem : "is scheduled by"
  Signal |o--|| ScheduleItem : "is scheduled by"

  ObstacleAndResponse }o--|| Obstacle : "creates and references"
  ObstacleAndResponse ||--|| Response : "owns"
```

### EveningLog

``` mermaid
---
title: EveningLog Entity Relationship Diagram
---
erDiagram
  direction TB

  EveningLog ||--|{ ScheduleItem : "reflects on today's"
  EveningLog ||--|{ ObstacleAndResponse : "reflects on today's"
  EveningLog }o--o{ Focus : "reflects on active"
  EveningLog ||--|{ PromptAndResponse : "creates and owns"

  PromptAndResponse }o--|| Prompt : "creates and/or references"
  PromptAndResponse ||--|| Response : "owns"
```

## Review and Focus Domain

Reviews are used to reflect on an experience, learn from it and derive adjustments
for an upcoming time period in the form of a Focus.

Each Review subtype will review a specific subset of objects in the Vision and Entry
domains through a ReviewObservation.

Each ReviewObservation will target one specific domain object. Reviews may have multiple
ReviewObservations. ReviewObservations are used to derive adjustments for a Focus.

``` mermaid
---
config:
  layout: elk
title: Review and Focus Domain
---
erDiagram
  direction TB

  Review }o--o{ Review : "gathers evidence from other"
  Review ||--o{ ReviewObservation : "creates and owns"
  Review ||--o| Focus : "may create a"
  ReviewObservation }o--|| Focus : "derives adjustments for"

  ReviewObservation }o--|| Focus : "may evaluate a"
  ReviewObservation }o--|| Vision : "may evaluate an"
  ReviewObservation }o--|| Outcome : "may evaluate an"
  ReviewObservation }o--|| Operation : "may evaluate an"
  ReviewObservation }o--|| Project : "may evaluate a"
  ReviewObservation }o--|| Commitment : "may evaluate a"

  Focus ||--|{ FocusPoint : "creates and owns"

  Outcome |o--o{ FocusPoint : "may be supported by"
  Operation |o--o{ FocusPoint : "may be supported by"
  Project |o--o{ FocusPoint : "may be supported by"
  Commitment |o--o{ FocusPoint : "may be supported by"

  FocusPoint ||--o{ Metric : "may create and own"
```

``` mermaid
---
title: Focus Inheritance Types
---
classDiagram
    direction LR

    class Focus {
        <<abstract>>
    }

    class WeeklyFocus
    class MonthlyFocus
    class QuarterlyFocus

    Focus <|-- WeeklyFocus
    Focus <|-- MonthlyFocus
    Focus <|-- QuarterlyFocus
```

### WeeklyReview

``` mermaid
---
title: WeeklyReview Entity Relationship Diagram
---
erDiagram
  direction TB
  
  WeeklyReview }o--o{ Log : "gathers evidence from this week's"
  WeeklyReview }o--o{ Task : "gathers evidence from this week's"
  WeeklyReview ||--o{ ReviewObservation : "creates and owns"

  ReviewObservation }o--|| WeeklyFocus : "may evaluate a"
  ReviewObservation }o--|| Project : "may evaluate a"
  ReviewObservation }o--|| Commitment : "may evaluate a"

  WeeklyReview ||--o| WeeklyFocus : "may create a"
```

### MonthlyReview

``` mermaid
---
title: MonthlyReview Entity Relationship Diagram
---
erDiagram
  direction TB

  MonthlyReview }o--o{ WeeklyReview : "gathers evidence from this month's"
  MonthlyReview ||--o{ ReviewObservation : "creates and owns"

  ReviewObservation }o--|| MonthlyFocus : "may evaluate a"
  ReviewObservation }o--|| Outcome : "may evaluate an"
  ReviewObservation }o--|| Operation : "may evaluate an"
  ReviewObservation }o--|| Project : "may evaluate a"

  MonthlyReview ||--o| MonthlyFocus : "may create a"
```

### QuarterlyReview

``` mermaid
---
title: QuarterlyReview Entity Relationship Diagram
---
erDiagram
  direction TB

  QuarterlyReview }o--o{ MonthlyReview : "gathers evidence from this quarter's"
  QuarterlyReview ||--o{ ReviewObservation : "creates and owns"

  ReviewObservation }o--|| QuarterlyFocus : "may evaluate a"
  ReviewObservation }o--|| Vision : "may evaluate a"
  ReviewObservation }o--|| Outcome : "may evaluate an"
  ReviewObservation }o--|| Operation : "may evaluate an"

  QuarterlyReview ||--o| QuarterlyFocus : "may create a"
```
