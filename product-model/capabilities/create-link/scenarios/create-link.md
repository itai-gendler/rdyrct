---
kind: primary
routes:
  web: Web app
  api: REST API
steps:
- text: The User enters a destination and, optionally, a title, UTM parameters and a QR style, on the shared domain or the organization's default domain
  kind: actor
  actor: user
  entities:
  - {entity: organization, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::links
    api:
      place: rest-api
- text: The Product checks the destination is a valid web address that is not another URL shortener, and lifts any UTM parameters out of it
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: web::workspace::links
    api:
      place: rest-api
- text: No link of the organization on that domain has the same destination and UTM parameters, and the plan's link limit has room
  kind: condition
  actor: user
  entities:
  - {entity: organization, effect: reads, facts: [Plan]}
  - {entity: link, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::links
    api:
      place: rest-api
- text: The Product creates the link with a random slug on the shared domain, or the chosen or a random slug on a custom domain, and starts redirecting
  kind: product
  actor: user
  entities:
  - {entity: link, effect: creates, to: Active, facts: [Slug, Domain, Short URL, Destination, Title, UTM parameters, QR style, Created by, Created, Clicks]}
  - {entity: custom-domain, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::links
    api:
      place: rest-api
- text: After answering, the Product checks the destination with a security resolver and records its risk score
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

# Create a link

## Trigger

A member wants a short address for a page.

## Outcome

The link exists and redirects; the plan's link count goes up by one.

## Edge cases

- A chosen slug already taken on that domain is refused and the slug field is pointed out.
- A chosen slug on the shared domain is refused: chosen slugs need a custom domain.
- A reserved word such as dashboard or login cannot be a slug.
- Styling the QR code on the Free plan is refused with a prompt to upgrade.
