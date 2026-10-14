---
kind: primary
routes:
  web: Web app
steps:
- text: The User changes the organization's QR look, uploading a logo of at most 256 KB and 512 pixels if wanted, and saves
  kind: actor
  actor: user
  entities:
  - {entity: organization, effect: reads, facts: [QR defaults]}
  contexts:
    web:
      place: web::workspace::organization
- text: The owner's plan is a paid plan
  kind: condition
  actor: user
  entities:
  - {entity: organization, effect: reads, facts: [Plan]}
  contexts:
    web:
      place: web::workspace::organization
- text: The Product saves the QR defaults and removes a replaced logo
  kind: product
  actor: user
  entities:
  - {entity: organization, effect: changes, facts: [QR defaults]}
  contexts:
    web:
      place: web::workspace::organization
---

# Change the organization's QR defaults

## Trigger

An admin brands every QR code at once.

## Outcome

Every QR code without its own style uses the new look.
