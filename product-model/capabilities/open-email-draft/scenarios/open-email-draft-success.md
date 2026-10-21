---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user chooses Open in Mail for the edited draft
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice opens the mail application with the draft
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
- kind: code
  role: implementation
  target: src/main/share/mailto.ts
---

# Open email draft in Mail

## Trigger

The user chooses Open in Mail for the edited draft.

## Outcome

Rice opens the mail application with the draft.

## Edge cases

- A mail link exceeding 8,000 characters is refused; Copy remains available.
- Rice does not send the email.
