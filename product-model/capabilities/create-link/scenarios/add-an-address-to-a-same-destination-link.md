---
kind: alternative
routes:
  web: Web app
steps:
- text: The User creates a link whose destination and UTM parameters match an existing link of the organization on the same domain
  kind: actor
  actor: user
  entities:
  - {entity: organization, effect: reads, facts: []}
  - {entity: link, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::links
- text: The Product offers the matching links instead of creating a second one
  kind: product
  actor: user
  entities:
  - {entity: link, effect: reads, facts: [Short URL, Destination, UTM parameters]}
  contexts:
    web:
      place: web::workspace::links
- text: The User chooses to add the address to the existing link
  kind: actor
  actor: user
  entities:
  - {entity: link, effect: reads, facts: [Short URL]}
  contexts:
    web:
      place: web::workspace::links
- text: The Product adds the chosen or random slug to that link as a permanent alias, so its settings and analytics stay together
  kind: product
  actor: user
  entities:
  - {entity: alias, effect: creates, to: Permanent, facts: [Slug, Short URL, Origin, Created]}
  - {entity: link, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::links
---

# Add the address to a link with the same destination

## Trigger

A member shortens a page the organization already has a link for.

## Outcome

One link answers on both addresses and its clicks stay in one place.

## Edge cases

- The member can instead create a separate link anyway.
- If the matched link changed destination meanwhile, the Product asks the member to review and try again.
