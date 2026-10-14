---
appliesTo:
- type: entity
  id: custom-domain
  effect: removes
references:
- kind: code
  role: implementation
  target: src/worker/routes/domains.ts#domainRoutes
---

# A custom domain that links still use cannot be deleted

Any active address on the domain, primary or alias, blocks deleting it.
