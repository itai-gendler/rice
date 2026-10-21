---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user confirms deletion of the meeting
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
- text: Rice moves the meeting to Trash and removes its associated memory facts
  kind: product
  entities:
  - entity: meeting
    effect: removes
    from: Done
  - entity: memory-fact
    effect: removes
    from: Open
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

# Delete a saved meeting

## Trigger

The user confirms Delete meeting.

## Outcome

The meeting leaves the Rice collection and its files are recoverable through the system Trash.

## Edge cases

- Canceling confirmation leaves the meeting unchanged.
- A Trash failure is reported.
