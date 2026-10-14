---
appliesTo:
- type: entity
  id: link
  effect: changes
  facts: [Domain]
references:
- kind: code
  role: implementation
  target: src/worker/routes/links.ts#linkRoutes
---

# A link's domain never changes

A link's aliases live on its domain, so moving the link would strand them. To use another domain, create a new link there.
