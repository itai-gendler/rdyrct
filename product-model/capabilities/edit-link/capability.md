---
availability:
- {place: 'web::workspace'}
- {place: rest-api}
- {place: mcp-server}
domain: links
references:
- kind: code
  role: implementation
  target: src/worker/routes/links.ts#mergedLinkUpdate
- kind: code
  role: implementation
  target: src/worker/routes/links.ts#resolveRenamedSlug
- kind: code
  role: implementation
  target: src/worker/plan.ts#guardedTempAliasStatement
- kind: code
  role: implementation
  target: src/worker/routes/mcp.ts#updateLink
---

# Edit link

Change a link's destination, title, UTM parameters, QR style, or on a custom domain its slug. A renamed custom-domain address keeps redirecting for 48 hours as a temporary alias. A link's domain never changes.
