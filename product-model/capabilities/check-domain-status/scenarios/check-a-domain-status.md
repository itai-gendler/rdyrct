---
kind: primary
routes:
  web: Web app
steps:
- text: The User checks the status of a custom domain
  kind: actor
  actor: user
  entities:
  - {entity: custom-domain, effect: reads, facts: [Hostname]}
  contexts:
    web:
      place: web::workspace::domains
- text: The Product shows its latest status and what changed since the last look
  kind: product
  actor: user
  entities:
  - {entity: custom-domain, effect: reads, facts: [Hostname, Status reason]}
  contexts:
    web:
      place: web::workspace::domains
---

# Check a custom domain's status

## Trigger

An admin waits for DNS to take effect.

## Outcome

The admin knows whether the custom domain is serving yet.
