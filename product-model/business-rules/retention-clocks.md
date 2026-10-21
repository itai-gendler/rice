---
appliesTo:
- type: entity
  id: meeting
references:
- kind: code
  role: implementation
  target: src/main/privacy/retention.ts
---

# Audio expiry uses the last end and whole-meeting expiry uses the first start

Audio retention starts from the last end time, falling back to start. Whole-meeting age is measured in calendar months from its start. Whole-meeting expiry takes precedence over audio expiry.
