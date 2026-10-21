---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user enters a follow-up and optional source and date
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop::follow-ups
  actor: user
- text: Rice creates an open manual memory fact for the follow-up
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
  contexts:
    desktop:
      place: desktop::follow-ups
  actor: user
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
- kind: code
  role: implementation
  target: src/main/memory/followups.ts
---

# Add follow-up

## Trigger

The user enters a follow-up and optional source and date.

## Outcome

Rice creates an open manual memory fact for the follow-up.

## Edge cases

- A follow-up does not need a linked meeting.
- An empty or too-short statement is not saved.
