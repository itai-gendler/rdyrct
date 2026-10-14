---
appliesTo:
- type: entity
  id: custom-domain
  effect: creates
references:
- kind: code
  role: implementation
  target: src/worker/routes/domains.ts#resolveNewHostname
---

# A hostname is connected to one organization at most

The instance's own hosts can never be connected.
