---
references:
- kind: code
  role: implementation
  target: src/main/app/main.ts#chatAnswer
- kind: code
  role: implementation
  target: src/main/store/meeting-files.ts
- kind: code
  role: implementation
  target: src/renderer/web-search.js
---

# Meeting chat

The saved questions and completed answers for one meeting.

## Information kept

- **Turns** — Questions and answers in order.
- **Web sources** — Titles and URLs accompanying answers that used web search.
- **Answer progress** — The current streamed answer or failure.
- **Web search** — The conversation’s search choice.
