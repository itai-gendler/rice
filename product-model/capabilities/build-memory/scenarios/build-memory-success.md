---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user chooses Build memory from older meetings
  kind: actor
  entities:
  - entity: meeting
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::memory-settings
  actor: user
- text: Rice starts the pass and shows its progress in Memory settings
  kind: product
  entities:
  - entity: settings
    effect: changes
    facts:
    - Memory progress
  contexts:
    desktop:
      place: desktop::memory-settings
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
  target: src/renderer/memory.js
---

# Build memory from older meetings

## Trigger

The user chooses Build memory from older meetings.

## Outcome

Rice starts the pass and shows its progress in Memory settings.

## Edge cases

- Meetings without notes and meetings already marked extracted are skipped.
- Progress reports the current meeting and completed count.
