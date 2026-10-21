---
kind: configuration
of: capability-scenario
takesEffect: The desktop platform is established when Rice starts.
stability: The supported settings stay tied to that running platform. Saved settings are read when the next relevant
  capture or transcription service starts.
alternatives:
- id: change-audio-settings-mac
  selectedWhen: Rice runs on macOS.
- id: change-audio-settings-windows
  selectedWhen: Rice runs on Windows.
references:
- kind: code
  role: implementation
  target: src/renderer/audio-settings.js
- kind: code
  role: implementation
  target: src/main/app/main.ts
---

# Audio settings by platform

macOS and Windows offer different microphone and transcription choices within Audio settings.
