---
appliesTo:
- type: entity
  id: link
references:
- kind: code
  role: implementation
  target: src/worker/storage.ts#desiredLink
---

# A suspended link redirects on none of its addresses

Suspension covers every address the link answers to, and survives any later edit, rename or alias change until a Platform admin restores it.
