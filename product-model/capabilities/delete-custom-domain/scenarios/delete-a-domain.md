---
kind: primary
routes:
  web: Web app
  api: REST API
steps:
- text: The User deletes a custom domain and confirms
  kind: actor
  actor: user
  entities:
  - {entity: custom-domain, effect: reads, facts: [Hostname]}
  contexts:
    web:
      place: web::workspace::domains
    api:
      place: rest-api
- text: No active address of any link is on it
  kind: condition
  actor: user
  entities:
  - {entity: link, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::domains
    api:
      place: rest-api
- text: The Product disconnects the hostname, stops serving it and deletes the custom domain
  kind: product
  actor: user
  entities:
  - {entity: custom-domain, effect: removes, from: Active}
  contexts:
    web:
      place: web::workspace::domains
    api:
      place: rest-api
---

# Delete a custom domain

## Trigger

An admin no longer uses a hostname.

## Outcome

The custom domain is gone and the plan's domain count goes down.
