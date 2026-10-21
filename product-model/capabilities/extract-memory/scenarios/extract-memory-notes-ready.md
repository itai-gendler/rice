---
kind: alternate
routes:
  desktop: Rice desktop
steps:
- text: A meeting’s notes become ready while memory is enabled.
  kind: condition
  entities:
  - entity: settings
    effect: reads
    facts:
    - Memory enabled
  - entity: meeting
    effect: reads
    facts: []
  - entity: notes
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::memory
  unattended: true
- text: Rice stores memory facts with their source meeting and updates resolved earlier follow-ups.
  kind: product
  entities:
  - entity: memory-fact
    effect: creates
    facts:
    - Text
    - Kind
    - Person
    - Company
    - Topic
    - Due date
    - Mine
    - Source
    - Completion
    - Edited
    - Manual
    to: Open
  - entity: notes
    effect: reads
    facts:
    - Content
  - entity: annotations
    effect: reads
    facts:
    - Text
  - entity: meeting
    effect: reads
    facts:
    - Date
    - Participants
    - Speaker names
  contexts:
    desktop:
      place: desktop::memory
references:
- kind: code
  role: implementation
  target: src/main/memory/service.ts
- kind: code
  role: implementation
  target: src/main/memory/extract.ts
- kind: code
  role: implementation
  target: src/main/memory/ipc.ts
---

# Remember facts from notes

## Trigger

A meeting’s notes become ready while memory is enabled.

## Outcome

Rice stores memory facts with their source meeting and updates resolved earlier follow-ups.

## Edge cases

- Only explicit deadlines become due dates, interpreted against the meeting date.
- Regenerating notes can re-extract this meeting while preserving manually edited facts.
- No available AI result leaves extraction for a later attempt.
