---
availability:
- {place: 'web::workspace'}
domain: links
references:
- kind: code
  role: implementation
  target: src/app/components/qr.tsx
- kind: code
  role: implementation
  target: src/app/lib/org-qr.ts
---

# Download QR code

Show a link's QR code, drawn from its QR style over the organization's QR defaults, and download it as PNG or SVG.
