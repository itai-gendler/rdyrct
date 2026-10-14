---
availability:
- {place: 'web::workspace'}
- {place: rest-api}
- {place: mcp-server}
references:
- kind: code
  role: implementation
  target: src/worker/routes/links.ts#linkRoutes
- kind: code
  role: implementation
  target: src/worker/routes/links.ts#mergeAddressIntoLink
- kind: code
  role: implementation
  target: src/worker/routes/links.ts#resolveNewSlug
- kind: code
  role: implementation
  target: src/worker/plan.ts#insertLinkWithinLimit
- kind: code
  role: implementation
  target: src/worker/risk.ts#scoreAndRecord
- kind: code
  role: implementation
  target: src/app/components/link-editor.tsx
- kind: code
  role: implementation
  target: src/app/components/same-destination-dialog.tsx
---

# Create link

Shorten a web address into a link of the organization. On the shared domain the slug is always random; on a custom domain it may be chosen. UTM parameters can be set or are lifted out of the address, the QR code can be styled on paid plans, and a destination the organization already links to on that domain is offered as an extra address of the existing link instead.
