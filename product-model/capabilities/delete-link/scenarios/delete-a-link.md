---
kind: primary
routes:
  web: Web app
  api: REST API
steps:
- text: The User deletes a link and confirms
  kind: actor
  actor: user
  entities:
  - {entity: link, effect: reads, facts: [Short URL]}
  contexts:
    web:
      place: web::workspace::links
    api:
      place: rest-api
- text: The Product deletes the link, its aliases and its clicks, and stops every address redirecting
  kind: product
  actor: user
  entities:
  - {entity: link, effect: removes, from: Active}
  - {entity: alias, effect: removes, from: Permanent, with: link}
  - {entity: click, effect: removes, with: link}
  contexts:
    web:
      place: web::workspace::links
    api:
      place: rest-api
---

# Delete a link

## Trigger

A member no longer needs a link.

## Outcome

The link is gone, its addresses answer not found, and the plan's link count goes down.
