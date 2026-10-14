---
kind: primary
routes:
  web: Web app
steps:
- text: The Visitor enters a web address and, optionally, a logo, colors and a pattern
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::qr-code-generator
- text: The Product draws the QR code live in the browser
  kind: product
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::qr-code-generator
- text: The Visitor downloads it as PNG or SVG
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::qr-code-generator
---

# Make and download a QR code on the public generator

## Trigger

A Visitor needs a QR code for print or a screen.

## Outcome

The Visitor has the QR code as an image file; nothing was stored.
