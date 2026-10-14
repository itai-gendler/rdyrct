---
appliesTo:
- type: entity
  id: click
references:
- kind: code
  role: implementation
  target: src/worker/clicks.ts#enqueueClick
- kind: code
  role: implementation
  target: src/worker/index.ts
- kind: doc
  role: context
  target: README.md
  title: Privacy-friendly analytics
---

# A click keeps country, referrer, device and time, and never an IP address

Clicks are kept for 400 days and then removed. An organization sees them only within its plan's analytics window.
