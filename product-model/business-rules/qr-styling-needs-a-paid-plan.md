---
appliesTo:
- type: entity
  id: link
  effect: changes
  facts: [QR style]
- type: entity
  id: organization
  effect: changes
  facts: [QR defaults]
references:
- kind: code
  role: implementation
  target: src/worker/routes/links.ts#assertQrAllowed
- kind: code
  role: implementation
  target: src/shared/types.ts#QR_LOGO_MAX_BYTES
---

# Changing how QR codes look needs a paid plan

Every plan gets QR codes. Changing their logo, pattern or colors, for a link or for the organization's defaults, needs Hobby or Pro; saving a link with its styling unchanged is always allowed. Logos are at most 256 KB and 512 pixels on a side.
