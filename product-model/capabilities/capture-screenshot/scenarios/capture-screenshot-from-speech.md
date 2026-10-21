---
kind: alternate
routes:
  desktop: Rice desktop
steps:
- text: New speech passes the local showing-something filter during an enabled recording.
  kind: condition
  entities:
  - entity: settings
    effect: reads
    facts:
    - Screenshots enabled
  contexts:
    desktop:
      place: desktop::meeting
  unattended: true
- text: After AI confirmation and a short delay Rice saves a screenshot linked to the triggering passage.
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

# Capture a visual reference

## Trigger

New speech passes the local showing-something filter during an enabled recording.

## Outcome

After AI confirmation and a short delay Rice saves a screenshot linked to the triggering passage.

## Edge cases

- The confirmation uses recent speech text; failure or a negative answer creates no capture.
- A near-duplicate automatic picture is retried once and otherwise omitted.
- Caption refinement may use an image-capable provider; otherwise the speech explanation remains.
