---
appliesTo:
- type: entity
  id: link
  effect: creates
- type: entity
  id: link
  effect: changes
  facts: [Slug]
references:
- kind: code
  role: implementation
  target: src/worker/routes/links.ts#resolveNewSlug
- kind: code
  role: implementation
  target: src/worker/routes/links.ts#resolveRenamedSlug
---

# Links on the shared domain always get random slugs

Chosen slugs exist only on custom domains, where the whole namespace is the organization's own, so the shared namespace cannot be squatted. A shared-domain link keeps its random slug for good.
