---
kind: validation
routes:
  desktop: Rice desktop
steps:
- text: The user selects a file
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice reports the attachment size limit
  kind: product
  entities:
  - entity: attachment
    effect: reads
    facts:
    - Size
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
  target: src/main/attachments/store.ts
- kind: code
  role: implementation
  target: src/main/attachments/ipc.ts
- kind: code
  role: implementation
  target: src/renderer/attachments.js
---

# Reject an oversized attachment

## Trigger

The user adds a file exceeding the file or meeting total limit.

## Outcome

Rice reports that file’s error and preserves already added attachments.
