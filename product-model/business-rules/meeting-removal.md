---
appliesTo:
- type: entity
  id: meeting
  effect: removes
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
  target: src/main/privacy/retention.ts
- kind: code
  role: implementation
  target: src/main/store/drafts.ts
permits:
- actors:
  - user
  when:
  - fact: Capture in use
    is: false
- unattended: true
  when:
  - state: Done
- unattended: true
  when:
  - state: Draft
---

# The user removes inactive meetings and Rice removes eligible expired or empty meetings

User deletion requires the selected meeting not to be the active capture. Retention skips recording, finishing, interrupted, damaged and busy meetings. Empty-draft cleanup requires a never-recorded draft with no user content.
