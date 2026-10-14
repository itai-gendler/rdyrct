---
kind: primary
routes:
  web: Web app
  api: REST API
steps:
- text: The User enters a bare hostname such as go.example.com
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::workspace::domains
    api:
      place: rest-api
- text: The hostname is well formed, is not the instance's own host, is not connected to any organization, and the plan has room for another custom domain
  kind: condition
  actor: user
  entities:
  - {entity: organization, effect: reads, facts: [Plan]}
  - {entity: custom-domain, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::domains
    api:
      place: rest-api
- text: The Product adds the custom domain, shows the CNAME record to create, and starts setting it up in the background
  kind: product
  actor: user
  entities:
  - {entity: custom-domain, effect: creates, to: Checking DNS, facts: [Hostname, Root redirect, Created]}
  contexts:
    web:
      place: web::workspace::domains
    api:
      place: rest-api
---

# Add a custom domain

## Trigger

An admin wants the organization's links on its own brand.

## Outcome

The custom domain is listed as checking DNS, with the record to create.

## Edge cases

- A hostname already connected anywhere on the instance is refused.
- On the Free plan the Product refuses and points to a paid plan.
