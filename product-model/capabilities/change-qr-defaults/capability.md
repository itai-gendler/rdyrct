---
availability:
- {place: 'web::workspace'}
domain: organization
references:
- kind: code
  role: implementation
  target: src/app/components/qr-defaults-card.tsx
- kind: code
  role: implementation
  target: src/worker/routes/qr-logos.ts#qrLogoRoutes
- kind: code
  role: implementation
  target: src/worker/routes/orgs.ts#applyQrPatch
---

# Change QR defaults

Set the logo, pattern, colors, corner style, background, eye color and logo size every QR code in the organization starts from. Needs a paid plan.
