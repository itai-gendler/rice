---
appliesTo:
- type: entity
  id: settings
- type: entity
  id: ai-connection
- type: entity
  id: calendar-connection
references:
- kind: code
  role: implementation
  target: src/main/privacy/local-mode.ts
- kind: code
  role: implementation
  target: src/main/app/main.ts
- kind: code
  role: implementation
  target: src/main/ai/factory.ts
---

# Fully local mode uses the Local model provider

Enabling Fully local requires Local model. While enabled, Rice keeps remote provider selection, web search, tools, remote calendar synchronization, update checks and model downloads unavailable.
