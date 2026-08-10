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
  Outcome }o--o{ Operation : "is supported by"
  Outcome }o--o{ Project : "is supported by"
  Outcome }o--o{ Commitment : "is supported by"

  Operation }o--o{ Project : "is supported by"
  Operation }o--o{ Commitment : "is supported by"
  Operation ||--o{ Task : "creates and owns"

  Project }o--o{ Commitment : "is supported by"
  Project ||--o{ Task : "creates and owns"

  Commitment ||--o{ Task : "creates and owns repeated"
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
  MorningLog |o--|| Mood : "creates and owns"
  MorningLog }o--o{ Focus : "references active focus"
  MorningLog }|--o{ Task : "references today's scheduled"
  MorningLog }|--o{ Commitment : "references today's scheduled"
  MorningLog ||--|{ Signal : "creates and owns"
  MorningLog ||--|{ ObstacleAndResponse : "creates and owns"

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

  EveningLog |o--|| Mood : "creates and owns"
  EveningLog ||--|{ GratitudePromptAndResponse : "creates and owns"
  %% TODO: what does it mean to reflect on active focuses?
  EveningLog }o--o{ Focus : "reflects on today's focus" 
  EveningLog }|--|{ SignalReview : "creates and owns"
  EveningLog }|--o{ Task : "reflects on today's scheduled"
  EveningLog }|--o{ Commitment : "reflects on today's scheduled"
  EveningLog ||--|{ ReflectionPromptAndResponse : "creates and owns"

  GratitudePromptAndResponse }o--|| GratitudePrompt : "creates and/or references"
  GratitudePromptAndResponse ||--|| Response : "owns"

  ReflectionPromptAndResponse }o--|| ReflectionPrompt : "creates and/or references"
  ReflectionPromptAndResponse ||--|| Response : "owns"

  SignalReview }o--|| Signal : "references"
```

### Review and Focus Domain

All Review subtypes implement this general flow. Each Review subtype will review specific
objects such as Projects, Tasks and Commitments, and will not review ALL objects in the
Vision Domain.

A ReviewObservation can evaluate any of these objects, but each ReviewObservation will
target one specific domain object.

``` mermaid
---
title: Review and Focus Domain
---
erDiagram
  direction TB
  
  Review ||--o{ ReviewObservation : "creates and owns"

  ReviewObservation }o--|| Focus : "may evaluate a"
  ReviewObservation }o--|| Outcome : "may evaluate an"
  ReviewObservation }o--|| Operation : "may evaluate an"
  ReviewObservation }o--|| Project : "may evaluate a"
  ReviewObservation }o--|| Commitment : "may evaluate a"

  Review ||--o| Focus : "may create a"

  Focus ||--|{ FocusPoint : "owns"
  Outcome }o--o{ FocusPoint : "is supported by"
  Operation }o--o{ FocusPoint : "is prioritized by"
  Project }o--o{ FocusPoint : "is prioritized by"
  Commitment }o--o{ FocusPoint : "is prioritized by"
```

### Weekly Review

``` mermaid
---
title: WeeklyReview Entity Relationship Diagram
---
erDiagram
  direction TB
  
  WeeklyReview ||--o{ ReviewObservation : "creates and owns"

  ReviewObservation }o--|| WeeklyFocus : "may evaluate a"
  ReviewObservation }o--|| Log : "may evaluate a"
  ReviewObservation }o--|| Project : "may evaluate a"
  ReviewObservation }o--|| Commitment : "may evaluate a"

  WeeklyReview ||--o| WeeklyFocus : "may create a"
```

### Monthly Review

``` mermaid
---
title: MonthlyReview Entity Relationship Diagram
---
erDiagram
  direction TB

  MonthlyReview ||--o{ ReviewObservation : "creates and owns"

  ReviewObservation }o--|| MonthlyFocus : "may evaluate a"
  ReviewObservation }o--|| WeeklyFocus : "may evaluate a"
  ReviewObservation }o--|| Outcome : "may evaluate an"
  ReviewObservation }o--|| Operation : "may evaluate an"
  ReviewObservation }o--|| Project : "may evaluate a"

  MonthlyReview ||--o| MonthlyFocus : "may create a"
```

### Quarterly Review

``` mermaid
---
title: QuarterlyReview Entity Relationship Diagram
---
erDiagram
  direction TB

  QuarterlyReview ||--o{ ReviewObservation : "creates and owns"

  ReviewObservation }o--|| QuarterlyFocus : "may evaluate a"
  ReviewObservation }o--|| MonthlyFocus : "may evaluate a"
  ReviewObservation }o--|| Vision : "may evaluate a"
  ReviewObservation }o--|| Outcome : "may evaluate an"
  ReviewObservation }o--|| Operation : "may evaluate an"
  QuarterlyReview }o--o{ Project : "references"

  QuarterlyReview ||--o| QuarterlyFocus : "may create a"
```
