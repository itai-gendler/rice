---
references:
- kind: code
  role: implementation
  target: src/main/store/global-chat.ts
- kind: code
  role: implementation
  target: src/main/search/global-chat.ts
- kind: code
  role: implementation
  target: src/renderer/global-chat.js
---

# All meetings chat

The shared conversation used for all-meeting and folder questions.

## Information kept

- **Turns** — The current conversation’s questions and answers.
- **Scope** — All meetings or a selected folder for each question.
- **Citations** — Source meetings and search terms retained with answers.
- **Web sources** — External source titles and URLs retained with answers.
- **Answer progress** — The currently streamed answer or failure.
- **Web search** — The conversation’s search choice.
