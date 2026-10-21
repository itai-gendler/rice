---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user asks to repair the meeting
  kind: actor
  entities:
  - entity: meeting
    effect: reads
    facts:
    - Title
    - Date
  contexts:
    desktop:
      place: desktop::library
  actor: user
- text: Rice reconstructs the meeting from its directory and remaining material
  kind: product
  entities:
  - entity: meeting
    effect: changes
    facts:
    - Title
    - Date
    - Capture in use
    - Capture running
    from: Needs repair
    to: Done
  - entity: notes
    effect: reads
    facts:
    - Content
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
  target: src/main/store/meta-repair.ts
---

# Repair to done

## Trigger

The user chooses Repair meeting on a Needs repair entry.

## Outcome

Rice rebuilds the meeting details and opens the repaired meeting.

## Edge cases

- Existing notes or finalized audio produce Done; otherwise the meeting is Interrupted.
