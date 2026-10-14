---
appliesTo:
- type: entity
  id: connected-app
  effect: removes
permits:
- related:
  - {verb: allows, entity: user}
references:
- kind: code
  role: implementation
  target: src/worker/routes/oauth-connections.ts#oauthConnectionRoutes
---

# A person disconnects only their own connected apps

Only the person who allowed a client disconnects it; deleting the account removes every allowance.
