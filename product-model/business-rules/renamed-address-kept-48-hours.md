---
appliesTo:
- type: entity
  id: alias
  effect: creates
  to: Temporary
references:
- kind: code
  role: implementation
  target: src/worker/util.ts#ALIAS_TTL_MS
- kind: code
  role: implementation
  target: src/worker/routes/links.ts#linkRoutes
---

# A renamed custom-domain address keeps redirecting for 48 hours

Renaming a custom-domain link leaves its old address as a temporary alias that redirects for 48 hours, does not count toward the plan, and can be kept forever.
