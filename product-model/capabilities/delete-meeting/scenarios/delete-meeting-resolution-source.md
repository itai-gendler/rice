---
kind: alternate
routes:
  desktop: Rice desktop
steps:
- text: The user confirms meeting deletion
  kind: actor
  entities:
  - entity: meeting
    effect: reads
    facts:
    - Title
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice removes the meeting and its own facts
  kind: product
  entities:
  - entity: meeting
    effect: removes
    from: Done
  - entity: memory-fact
    effect: removes
    from: Open
    as: originating
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice reopens an earlier memory fact resolved by the deleted meeting
  kind: product
  entities:
  - entity: memory-fact
    effect: changes
    facts:
    - Completion
    from: Done
    to: Open
    as: earlier
  - entity: meeting
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
references:
- kind: code
  role: implementation
  target: src/renderer/renderer.js
- kind: code
  role: implementation
  target: src/main/app/main.ts
- kind: code
  role: implementation
  target: src/main/app/delete-meeting.ts
- kind: code
  role: implementation
  target: src/main/store/drafts.ts
- kind: code
  role: implementation
  target: src/main/privacy/retention.ts
---

# Delete a completing meeting

## Trigger

The user confirms deleting a meeting that resolved an earlier follow-up.

## Outcome

The deleted meeting’s facts disappear and affected earlier follow-ups reopen.
