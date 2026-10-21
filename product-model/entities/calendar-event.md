---
references:
- kind: code
  role: implementation
  target: src/main/calendar/calendar-feed.ts
- kind: code
  role: implementation
  target: src/main/calendar/google-events.ts
- kind: code
  role: implementation
  target: src/renderer/home.js
---

# Calendar event

A read-only event received from connected calendars.

## Information kept

- **Title** — Event name.
- **Time** — Start and end time and all-day indication.
- **Participants** — Names and addresses supplied by the calendar.
- **Join link** — The meeting URL when available.
- **Source** — The connected calendar source.
