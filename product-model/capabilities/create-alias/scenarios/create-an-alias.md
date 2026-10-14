---
kind: primary
routes:
  web: Web app
steps:
- text: The User adds an alias to a link, with a chosen slug when the link is not on the shared domain, or a random one
  kind: actor
  actor: user
  entities:
  - {entity: link, effect: reads, facts: [Short URL, Domain]}
  - {entity: alias, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::links
- text: The link has fewer than five aliases, the slug is free on the link's domain, and the plan's link limit has room
  kind: condition
  actor: user
  entities:
  - {entity: organization, effect: reads, facts: [Plan]}
  - {entity: link, effect: reads, facts: []}
  - {entity: alias, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::links
- text: The Product adds the permanent alias and starts redirecting it
  kind: product
  actor: user
  entities:
  - {entity: alias, effect: creates, to: Permanent, facts: [Slug, Short URL, Origin, Created]}
  contexts:
    web:
      place: web::workspace::links
---

# Create an alias

## Trigger

A member wants a second address for the same destination, such as a printed one.

## Outcome

The link answers on the new address too, with the same destination and analytics.

## Edge cases

- A sixth alias is refused until one is removed.
