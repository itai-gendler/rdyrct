---
kind: primary
routes:
  web: Web app
  api: REST API
steps:
- text: The User changes the destination, title, UTM parameters or QR style of a link and saves
  kind: actor
  actor: user
  entities:
  - {entity: link, effect: reads, facts: [Destination, Title]}
  contexts:
    web:
      place: web::workspace::links
    api:
      place: rest-api
- text: The Product saves the changes and republishes every address of the link
  kind: product
  actor: user
  entities:
  - {entity: link, effect: changes, facts: [Destination, Title, UTM parameters, QR style]}
  contexts:
    web:
      place: web::workspace::links
    api:
      place: rest-api
- text: When the destination changed, the Product clears its risk score and checks the new destination after answering
  kind: product
  actor: user
  entities:
  - {entity: link, effect: changes, facts: [Risk score, Risk reasons, Risk checked]}
  contexts:
    web:
      place: web::workspace::links
    api:
      place: rest-api
---

# Edit a link

## Trigger

A member corrects or retargets a link.

## Outcome

Every address of the link redirects to the new destination with the new UTM parameters.

## Edge cases

- Changing how the QR code looks needs a paid plan; saving other fields with the existing styling unchanged is always allowed.
- A suspended link stays suspended through any edit.
