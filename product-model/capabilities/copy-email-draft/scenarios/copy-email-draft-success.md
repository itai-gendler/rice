---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user edits the email draft and chooses Copy
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice copies the edited draft text
  kind: product
  entities: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
references:
- kind: code
  role: implementation
  target: src/main/share/actions.ts
- kind: code
  role: implementation
  target: src/renderer/share.js
---

# Copy email draft

## Trigger

The user edits the email draft and chooses Copy.

## Outcome

Rice copies the edited draft text.
