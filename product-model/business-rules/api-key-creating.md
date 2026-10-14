---
appliesTo:
- type: entity
  id: api-key
  effect: creates
permits:
- related:
  - {verb: owns, entity: user}
references:
- kind: code
  role: implementation
  target: src/worker/routes/api-keys.ts#apiKeyRoutes
---

# A person creates API keys only for themselves

An API key belongs to the person who created it and acts as them in every organization they belong to. Creating one is offered on the API page of an organization the person owns.
