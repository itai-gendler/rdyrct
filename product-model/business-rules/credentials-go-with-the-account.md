---
appliesTo:
- type: entity
  id: api-key
  effect: removes
permits:
- related:
  - {verb: owns, entity: user}
references:
- kind: code
  role: implementation
  target: src/worker/db/schema.ts#apiKeys
---

# A person's API keys go only with their own account

Deleting an account deletes its API keys; nobody else deletes them.
