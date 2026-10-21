---
entities:
- entity: calendar-event
  shows:
  - Title
  - Time
  - Participants
  - Join link
  - Source
- entity: meeting
  shows:
  - Title
  - Date
- entity: memory-fact
  shows:
  - Text
  - Person
  - Company
  - Due date
  - Source
references:
- kind: code
  role: implementation
  target: src/renderer/home.js
---

# Home

Upcoming calendar meetings, recording entry points and preparation briefs.
