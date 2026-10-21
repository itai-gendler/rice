---
appliesTo:
- type: entity
  id: screenshot
  effect: creates
references:
- kind: code
  role: implementation
  target: src/main/screenshots/capture.ts
- kind: code
  role: implementation
  target: src/main/app/main.ts
permits:
- actors:
  - user
  when:
  - entity: settings
    fact: Screenshots enabled
    is: true
  - entity: meeting
    fact: Capture running
    is: true
- unattended: true
  when:
  - entity: settings
    fact: Screenshots enabled
    is: true
  - entity: meeting
    fact: Capture running
    is: true
---

# The user and Rice create screenshots only when capture is enabled

Capture runs only during unpaused recording with Screenshots enabled. Manual capture is immediate; automatic capture requires a showing-something speech trigger and AI confirmation.
