---
kind: primary
routes:
  web: Web app
steps:
- text: The User opens a link's QR code
  kind: actor
  actor: user
  entities:
  - {entity: link, effect: reads, facts: [Short URL, QR style]}
  contexts:
    web:
      place: web::workspace::links
- text: The Product draws the QR code for the link's short address in the link's style, falling back to the organization's QR defaults
  kind: product
  actor: user
  entities:
  - {entity: link, effect: reads, facts: [Short URL, QR style]}
  - {entity: organization, effect: reads, facts: [QR defaults]}
  contexts:
    web:
      place: web::workspace::links
- text: The User downloads it as PNG or SVG
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::workspace::links
---

# Download a link's QR code

## Trigger

A member needs the link's QR code for print or a screen.

## Outcome

The member has the QR code image; scanning it follows the link.
