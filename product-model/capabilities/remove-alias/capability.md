---
availability:
- {place: 'web::workspace'}
domain: links
references:
- kind: code
  role: implementation
  target: src/worker/routes/links.ts#linkRoutes
- kind: code
  role: implementation
  target: src/worker/storage.ts#sweepExpiredAliases
---

# Remove alias

Retire an alias so it stops redirecting at once and its slug is free again. The primary address cannot be removed this way. Temporary aliases retire on their own after 48 hours.
