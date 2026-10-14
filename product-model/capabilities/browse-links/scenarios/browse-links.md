---
kind: primary
routes:
  web: Web app
  api: REST API
steps:
- text: The User opens the links, optionally searching, filtering by domain or sorting
  kind: actor
  actor: user
  entities:
  - {entity: link, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::links
    api:
      place: rest-api
- text: The Product lists the organization's links, newest first unless sorted otherwise, a page at a time
  kind: product
  actor: user
  entities:
  - {entity: link, effect: reads, facts: [Short URL, Destination, Title, Clicks, Created, Created by]}
  - {entity: organization, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::links
    api:
      place: rest-api
---

# Browse the organization's links

## Trigger

A member looks for a link or reviews them all.

## Outcome

The member sees the links that match, with their clicks.
