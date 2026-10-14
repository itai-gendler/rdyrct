---
kind: alternative
routes:
  web: Web app
  api: REST API
steps:
- text: The User changes the slug of a link that is not on the shared domain
  kind: actor
  actor: user
  entities:
  - {entity: link, effect: reads, facts: [Slug, Domain]}
  contexts:
    web:
      place: web::workspace::links
    api:
      place: rest-api
- text: The new slug is free on that domain and is not already one of the link's own aliases
  kind: condition
  actor: user
  entities:
  - {entity: link, effect: reads, facts: []}
  - {entity: alias, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::links
    api:
      place: rest-api
- text: The Product gives the link the new slug and keeps the old address as a temporary alias that redirects for 48 hours
  kind: product
  actor: user
  entities:
  - {entity: link, effect: changes, facts: [Slug, Short URL]}
  - {entity: alias, effect: creates, to: Temporary, facts: [Slug, Short URL, Origin, Expires, Created]}
  contexts:
    web:
      place: web::workspace::links
    api:
      place: rest-api
---

# Rename a link on a custom domain

## Trigger

A member wants a better address for a branded link.

## Outcome

The link answers on its new slug, and its old one keeps working for 48 hours.

## Edge cases

- Choosing a slug that is already the link's alias is refused with a hint to make that alias primary instead.
- Links on the shared domain keep their random slug.
