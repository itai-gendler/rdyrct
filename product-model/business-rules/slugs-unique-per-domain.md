---
appliesTo:
- type: entity
  id: link
  effect: creates
- type: entity
  id: alias
  effect: creates
references:
- kind: code
  role: implementation
  target: src/worker/util.ts#SLUG_RE
- kind: code
  role: implementation
  target: src/worker/util.ts#RESERVED_SLUGS
- kind: code
  role: implementation
  target: src/worker/routes/links.ts#slugTaken
---

# A slug answers for one address per domain

No two active addresses share a slug on the same domain; retired aliases free their slug. Slugs are letters, digits, hyphens and underscores, up to 64, and the app's own words such as dashboard, links or login are reserved.
