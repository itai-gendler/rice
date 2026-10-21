---
references:
- kind: code
  role: implementation
  target: src/main/ai/service.ts
- kind: code
  role: implementation
  target: src/main/app/main.ts
---

# AI connection

A configured AI provider used through a supported subscription, API key or local model server.

## Information kept

- **Provider** — Claude, ChatGPT, Gemini, OpenCode, Antigravity or Local model.
- **Method** — The supported subscription, key or local-server connection method.
- **Credential status** — Whether required credentials are present; saved keys show only a suffix.
- **Test result** — The last connection check and any actionable error.
- **Models** — Available models for this connection.
