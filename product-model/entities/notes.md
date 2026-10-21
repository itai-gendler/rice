---
references:
- kind: code
  role: implementation
  target: src/main/session/notes.ts
- kind: code
  role: implementation
  target: src/main/session/long-notes.ts
---

# Notes

The current generated notes for a meeting.

## Information kept

- **Content** — The current Markdown summary, highlighted user jottings and task checkboxes.
- **Progress** — Generation stage and part progress or the latest failure.

## States

### Empty

No generated notes are available.

### Generating

Rice is extracting or writing notes; an earlier version may remain readable.

### Ready

The current generated notes are available.

### Failed

Generation did not produce notes and can be retried.
