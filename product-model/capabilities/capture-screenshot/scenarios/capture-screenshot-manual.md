---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user chooses Capture now
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice creates a screenshot linked to the transcript
  kind: product
  entities:
  - entity: screenshot
    effect: creates
    facts:
    - Image
    - Time
    - Caption
    - Trigger
    - Transcript position
  - entity: transcript
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
  target: src/main/screenshots/capture.ts
- kind: code
  role: implementation
  target: src/main/screenshots/ipc.ts
- kind: code
  role: implementation
  target: src/renderer/screenshots.js
---

# Capture now

## Trigger

The user chooses Capture now during an unpaused recording with capture enabled.

## Outcome

Rice stores the picture beside its nearest transcript passage.

## Edge cases

- Manual capture does not discard the picture merely because it resembles the previous one.
- No screen permission or capture failure yields no new image.
