---
appliesTo:
- type: entity
  id: all-meetings-chat
references:
- kind: code
  role: implementation
  target: src/main/store/global-chat.ts
---

# A new global conversation resets context without deleting old turns

Current all-meetings chat starts after the last New conversation marker; earlier local turns remain stored.
