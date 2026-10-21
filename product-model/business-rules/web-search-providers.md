---
appliesTo:
- type: entity
  id: meeting-chat
- type: entity
  id: all-meetings-chat
references:
- kind: code
  role: implementation
  target: src/main/ai/web-search.ts
- kind: code
  role: implementation
  target: src/main/app/main.ts
---

# Web search uses supported online providers

Web search is available through Claude subscription, ChatGPT subscription and the Claude, OpenAI and Gemini APIs while Fully local mode is off. Local model, OpenCode and Antigravity do not offer this search option.
