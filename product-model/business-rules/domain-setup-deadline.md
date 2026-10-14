---
appliesTo:
- type: entity
  id: custom-domain
  effect: changes
  to: Error
references:
- kind: code
  role: implementation
  target: src/worker/routes/domains.ts#probeDomain
---

# A custom domain that is not serving within a day fails

Setup gives DNS and the certificate one day; after that the custom domain shows an error and has to be added again.
