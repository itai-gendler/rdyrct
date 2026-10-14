---
kind: person
acts: external
relations:
- {entity: account, verb: uses, cardinality: one-to-one}
- {entity: membership, verb: holds, cardinality: one-to-many}
- {entity: api-key, verb: owns, cardinality: one-to-many}
- {entity: connected-app, verb: allows, cardinality: one-to-many}
- {entity: ai-agent, verb: connects, cardinality: one-to-many}
references:
- kind: code
  role: implementation
  target: src/worker/session.ts#withSession
- kind: code
  role: implementation
  target: src/worker/env.ts
---

# User

A person signed in to their account. What a User may do in an organization depends on the Role their membership there holds; the same person may own one organization and be a viewer in another.
