---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user selects an attachment
  kind: actor
  entities:
  - entity: attachment
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice displays attachment details and opens or reveals the chosen file
  kind: product
  entities:
  - entity: attachment
    effect: reads
    facts:
    - Name
    - Content
    - Kind
    - Size
    - Added
    - Text availability
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
  target: src/main/attachments/ipc.ts
- kind: code
  role: implementation
  target: src/renderer/attachments.js
---

# Browse attachments

## Trigger

The user selects an attachment.

## Outcome

Rice displays attachment details and opens or reveals the chosen file.
