---
appliesTo:
- type: entity
  id: settings
- type: entity
  id: meeting-chat
- type: entity
  id: all-meetings-chat
- type: entity
  id: meeting
references:
- kind: code
  role: implementation
  target: src/main/app/main.ts#toolsAllowed
- kind: code
  role: implementation
  target: src/main/warroom/ipc.ts#supportFor
---

# Chat tools require an enabled supported subscription connection

Tools and MCPs in chat require the user option enabled, Fully local mode off and Claude or ChatGPT subscription. Notes, email drafting and part extraction do not use chat tools. Investigation sources separately depend on enabled supported sources.
