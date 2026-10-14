---
appliesTo:
- type: entity
  id: api-key
  effect: changes
permits:
- related:
  - {verb: owns, entity: user}
references:
- kind: code
  role: implementation
  target: src/worker/routes/api-keys.ts#apiKeyRoutes
---

# A person revokes only their own API keys

Nobody else, in any organization, revokes a person's key.
