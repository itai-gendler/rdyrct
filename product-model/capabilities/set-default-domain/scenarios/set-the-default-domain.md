---
kind: primary
routes:
  web: Web app
steps:
- text: The User makes an active custom domain the default
  kind: actor
  actor: user
  entities:
  - {entity: custom-domain, effect: reads, facts: [Hostname]}
  contexts:
    web:
      place: web::workspace::domains
- text: The custom domain belongs to the organization, is active and is not locked
  kind: condition
  actor: user
  entities:
  - {entity: custom-domain, effect: reads, facts: [Locked]}
  - {entity: organization, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::domains
- text: The Product makes it the organization's default domain, which every new one then starts on
  kind: product
  actor: user
  entities:
  - {entity: organization, effect: changes, facts: [Default domain]}
  contexts:
    web:
      place: web::workspace::domains
---

# Default new links to a custom domain

## Trigger

An admin wants every new link branded without picking the domain each time.

## Outcome

New links start on the custom domain.
