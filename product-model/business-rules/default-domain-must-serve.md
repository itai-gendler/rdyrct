---
appliesTo:
- type: entity
  id: organization
  effect: changes
  facts: [Default domain]
references:
- kind: code
  role: implementation
  target: src/worker/routes/orgs.ts#resolveDefaultDomain
---

# Only an active, unlocked custom domain of the organization can be the default

A domain still setting up, in error or locked would hand new links an address that does not work.
