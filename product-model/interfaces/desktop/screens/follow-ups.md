---
entities:
- entity: memory-fact
  shows:
  - Text
  - Person
  - Due date
  - Mine
  - Source
  - Completion
  collects:
  - Text
  - Due date
  - Person
  - Mine
references:
- kind: code
  role: implementation
  target: src/renderer/followups.js
---

# Follow-ups

Open and completed commitments and requests, with ownership and deadlines.
