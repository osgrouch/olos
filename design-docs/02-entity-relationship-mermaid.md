# Entity Relationships with Mermaid

## Visions Domain
``` mermaid
---
config:
  layout: elk
title: Visions Domain
---
erDiagram
  direction TB

  VISION ||--o{ OUTCOME : "creates and owns"

  OUTCOME }o--o{ OUTCOME : "can block other"
  OUTCOME }o--o{ OPERATION : "is supported by"
  OUTCOME }o--o{ PROJECT : "is supported by"
  OUTCOME }o--o{ COMMITMENT : "is supported by"

  OPERATION }o--o{ PROJECT : "is supported by"
  OPERATION }o--o{ COMMITMENT : "is supported by"
  OPERATION ||--o{ TASK : "creates and owns"

  PROJECT }o--o{ COMMITMENT : "is supported by"
  PROJECT ||--o{ TASK : "creates and owns"

  COMMITMENT ||--o{ TASK : "creates and owns repeated"
```

## Entries Domain

``` mermaid
---
title: Entry Inheritence Types
---
erDiagram
  direction LR

  Entry ||--o{ Log : "can be of type"
  Entry ||--o{ Review : "can be of type"

  Log ||--o{ MorningLog : "can be of type"
  Log ||--o{ EveningLog : "can be of type"

  Review ||--o{ WeeklyReview : "can be of type"
  Review ||--o{ MonthlyReview : "can be of type"
  Review ||--o{ QuarterlyReview : "can be of type"

  Focus ||--o{ WeeklyFocus : "can be of type"
  Focus ||--o{ MonthlyFocus : "can be of type"
  Focus ||--o{ QuarterlyFocus : "can be of type"
```

### Morning Log

``` mermaid
---
title: MorningLog Relationships
---
erDiagram
  direction TB

  MorningLog |o--|| Mood : "creates and owns"
  MorningLog ||--|| SleepRecord: "creates and owns"
  MorningLog }|--|| WeeklyFocus : "references this week's"
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
title: EveningLog Relationships
---
erDiagram
  direction TB

  EveningLog |o--|| Mood : "creates and owns"
  EveningLog ||--|{ GratitudePromptAndResponse : "creates and owns"
  EveningLog }|--|{ Signal : "reflects on today's"
  EveningLog }|--o{ Task : "reflects on today's scheduled"
  EveningLog }|--o{ Commitment : "reflects on today's scheduled"
  EveningLog ||--|{ ReflectionPromptAndResponse : "creates and owns"

  GratitudePromptAndResponse }o--|| GratitudePrompt : "creates and/or references"
  GratitudePromptAndResponse ||--|| Response : "owns"

  ReflectionPromptAndResponse }o--|| ReflectionPrompt : "creates and/or references"
  ReflectionPromptAndResponse ||--|| Response : "owns"
```

### Weekly Review

``` mermaid
---
title: WeeklyReview Relationships
---
erDiagram
  direction TB

  WeeklyReview }|--|| WeeklyFocus : "reflects on previous and creates new"
  WeeklyReview }|--o{ Project : "reflects on progress and updates"
  WeeklyReview }|--o{ Task : "reflects on previous week and schedules for upcoming week"
  WeeklyReview }|--o{ Commitment : "reflects on previous week and schedules for upcoming week"
```

### Monthly Review

``` mermaid
---
title: MonthlyReview Relationships
---
erDiagram
  direction TB

  MonthlyReview ||--|{ WeeklyFocus : "reviews this month's"
  MonthlyReview }|--|| MonthlyFocus : "reflects on previous and creates new"
  MonthlyReview }|--o{ Outcome : "reflects on, adjusts and can create new"
  MonthlyReview }|--o{ Operation : "reflects on, adjusts and can create new"
  MonthlyReview }|--o{ Project : "reflects on progress and updates"
```

### Quarterly Review

``` mermaid
---
title: QuarterlyReview Relationships
---
erDiagram
  direction TB
  
  QuarterlyReview ||--|{ MonthlyFocus : "reviews this quarter's"
  QuarterlyReview }|--|| QuarterlyFocus : "reviews previous and creates new"
  QuarterlyReview }|--o{ Vision : "reflects on, adjusts and can create new"
  QuarterlyReview }|--o{ Outcome : "reflects on, adjusts and can create new"
  QuarterlyReview }|--o{ Operation : "reflects on, adjusts and can create new"
```
