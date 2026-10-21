---
kind: alternate
routes:
  desktop: Rice desktop
steps:
- text: The startup or daily retention sweep finds a completed meeting whose effective whole-meeting deadline has
    passed.
  kind: condition
  entities:
  - entity: folder
    effect: reads
    facts:
    - Meeting retention
  - entity: settings
    effect: reads
    facts:
    - Default retention
  - entity: meeting
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::meeting
  unattended: true
- text: Rice moves the expired meeting to Trash and reports the applied retention rule.
  kind: product
  entities:
  - entity: meeting
    effect: removes
    from: Done
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
  target: src/main/app/delete-meeting.ts
- kind: code
  role: implementation
  target: src/main/store/drafts.ts
- kind: code
  role: implementation
  target: src/main/privacy/retention.ts
---

# Apply whole-meeting retention

## Trigger

The startup or daily retention sweep finds a completed meeting whose effective whole-meeting deadline has passed.

## Outcome

Rice moves the expired meeting to Trash and reports the applied retention rule.

## Edge cases

- Recording, finishing, interrupted, damaged and currently busy meetings are skipped.
- An explicitly configured Keep forever overrides an inherited expiry.
