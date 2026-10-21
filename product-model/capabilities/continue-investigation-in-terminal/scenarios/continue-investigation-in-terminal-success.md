---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user chooses Continue in terminal or Copy prompt
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice prepares the handoff from meeting file paths and pinned findings
  kind: product
  entities:
  - entity: meeting
    effect: reads
    facts:
    - Title
  - entity: transcript
    effect: reads
    facts:
    - Content
  - entity: finding
    effect: reads
    facts:
    - Text
    - Source
    - Pinned
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
references:
- kind: code
  role: implementation
  target: src/main/warroom/ipc.ts
- kind: code
  role: implementation
  target: src/main/warroom/engine.ts
- kind: code
  role: implementation
  target: src/renderer/warroom.js
- kind: code
  role: implementation
  target: src/main/warroom/handoff.ts
---

# Continue investigation in terminal

## Trigger

The user chooses Continue in terminal or Copy prompt.

## Outcome

Rice prepares the handoff from meeting file paths and pinned findings.

## Edge cases

- The prompt contains paths rather than the transcript text.
- The user chooses a work folder before continuing.
- Canceling folder selection leaves the investigation unchanged.
- An unavailable CLI or terminal failure is reported; Rice keeps recording.
