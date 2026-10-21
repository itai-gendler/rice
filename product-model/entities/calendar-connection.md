---
references:
- kind: code
  role: implementation
  target: src/main/app/main.ts
- kind: code
  role: implementation
  target: src/main/calendar/calendar-feed.ts
- kind: code
  role: implementation
  target: src/main/calendar/ics-feed.ts
---

# Calendar connection

An optional calendar source used to prepare and detect meetings.

## Information kept

- **Source** — macOS Calendar, Google or an ICS subscription.
- **Status** — Connection or permission status and latest refresh error.
- **Calendars** — Calendar count when available.
- **Address label** — The displayed source domain for an ICS connection.
