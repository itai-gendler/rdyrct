---
kind: primary
routes:
  web: Web app
steps:
- text: The User enters a web address as the custom domain's root redirect, or clears it
  kind: actor
  actor: user
  entities:
  - {entity: custom-domain, effect: reads, facts: [Root redirect]}
  contexts:
    web:
      place: web::workspace::domains
- text: The address is a valid http or https address
  kind: condition
  actor: user
  entities: []
  contexts:
    web:
      place: web::workspace::domains
- text: The Product saves it and, for an active custom domain, starts using it at once
  kind: product
  actor: user
  entities:
  - {entity: custom-domain, effect: changes, facts: [Root redirect]}
  contexts:
    web:
      place: web::workspace::domains
---

# Change a custom domain's root redirect

## Trigger

An admin wants the bare branded domain to land on the company site.

## Outcome

Visits to the custom domain's root go to the chosen page.
