---
availability:
- {place: 'web::workspace'}
- {place: rest-api}
- {place: mcp-server}
- {place: 'web::admin-console'}
references:
- kind: code
  role: implementation
  target: src/worker/routes/links.ts#linkRoutes
- kind: code
  role: implementation
  target: src/worker/routes/admin-links.ts#adminLinkRoutes
- kind: code
  role: implementation
  target: src/worker/routes/mcp.ts#deleteLink
---

# Delete link

Delete a link with all its addresses, its QR logo and its click history. Every address stops redirecting at once. Platform admins delete a link from the admin console when suspending is not enough.
