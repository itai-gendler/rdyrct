---
appliesTo:
- type: entity
  id: connected-app
  effect: creates
permits:
- related:
  - {verb: allows, entity: user}
references:
- kind: code
  role: implementation
  target: src/app/routes/consent.tsx
---

# A person allows AI agent clients only for themselves

An AI agent client acts for the person who allowed it, with what that person may do.
