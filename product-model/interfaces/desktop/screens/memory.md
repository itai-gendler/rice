---
entities:
- entity: memory-fact
  shows:
  - Text
  - Kind
  - Person
  - Company
  - Topic
  - Due date
  - Source
  - Completion
  - Mine
  collects:
  - Text
references:
- kind: code
  role: implementation
  target: src/renderer/memory-page.js
- kind: code
  role: implementation
  target: src/renderer/memory.js
---

# Memory

Remembered people and companies, their facts and linked source meetings.
