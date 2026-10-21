---
entities:
- entity: ai-connection
  shows:
  - Provider
  - Method
  - Credential status
  - Test result
  - Models
- entity: settings
  shows:
  - AI provider
  - AI model
  - Light model
  - Local server
  - Cycle limit
  collects:
  - AI provider
  - AI model
  - Light model
  - Local server
  - Cycle limit
references:
- kind: code
  role: implementation
  target: src/renderer/ai-providers.js
- kind: code
  role: implementation
  target: src/renderer/settings.js
---

# Artificial intelligence settings

Provider setup, test results and primary and light model choices.
