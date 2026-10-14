---
kind: alternative
routes:
  web: Web app
steps:
- text: A newly added custom domain's CNAME record resolves
  kind: condition
  unattended: true
  entities:
  - {entity: custom-domain, effect: reads, facts: [Hostname]}
  contexts:
    web:
      place: web::workspace::domains
- text: The Product moves it on to issuing the certificate
  kind: product
  entities:
  - {entity: custom-domain, effect: changes, from: Checking DNS, to: Issuing TLS, facts: []}
  contexts:
    web:
      place: web::workspace::domains
- text: Once the certificate is issued, the Product marks the custom domain active and starts serving its short links
  kind: product
  entities:
  - {entity: custom-domain, effect: changes, from: Issuing TLS, to: Active, facts: []}
  - {entity: link, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::domains
---

# A custom domain finishes setup

## Trigger

The organization's DNS record takes effect.

## Outcome

The custom domain serves short links; checking is fast at first and then every few minutes.
