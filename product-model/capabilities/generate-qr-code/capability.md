---
availability:
- {place: 'web::public'}
- {place: mcp-server}
references:
- kind: code
  role: implementation
  target: src/app/routes/qr-generator.tsx
- kind: code
  role: implementation
  target: src/app/components/qr.tsx
- kind: code
  role: implementation
  target: src/worker/routes/mcp.ts#generateQrCode
---

# Generate a QR code

Make a QR code for any web address and download it as PNG or SVG. On the public generator the person can add a logo and choose colors and pattern; nothing is saved. The MCP server's tool returns a plain PNG for a given address.
