---
availability:
- {place: 'web::admin-console'}
domain: platform-links
references:
- kind: code
  role: implementation
  target: src/worker/routes/admin-links.ts#adminLinkRoutes
---

# Delete anonymous link

Delete a short address made on the home page without an account, so it stops redirecting before its 24 hours are up.
