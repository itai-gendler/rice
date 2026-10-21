---
appliesTo:
- type: entity
  id: meeting
references:
- kind: code
  role: implementation
  target: src/main/session/meeting-session.ts
- kind: code
  role: implementation
  target: src/main/app/main.ts
---

# Only one recording captures at a time

Rice refuses a second start while capture is active. After capture is released, another meeting can start while the earlier meeting finishes.
