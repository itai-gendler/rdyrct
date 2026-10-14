---
kind: edge
routes:
  web: Web app
steps:
- text: A day after it was added the custom domain still has no resolving record or no certificate
  kind: condition
  unattended: true
  entities:
  - {entity: custom-domain, effect: reads, facts: [Created]}
  contexts:
    web:
      place: web::workspace::domains
- text: The Product marks it as an error with the reason, and stops checking
  kind: product
  entities:
  - {entity: custom-domain, effect: changes, from: Checking DNS, to: Error, facts: [Status reason]}
  contexts:
    web:
      place: web::workspace::domains
---

# A custom domain does not finish setup within a day

## Trigger

The DNS record never appears.

## Outcome

The custom domain shows the error and has to be deleted and added again.
