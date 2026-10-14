---
kind: primary
routes:
  web: Web app
steps:
- text: The User chooses Upgrade to Hobby or Upgrade to Pro
  kind: actor
  actor: user
  entities:
  - {entity: account, effect: reads, facts: [Plan]}
  contexts:
    web:
      place: web::workspace::billing
- text: The Product opens the billing provider's checkout for that plan with the person's email
  kind: product
  actor: user
  entities:
  - {entity: account, effect: reads, facts: [Email]}
  - {entity: billing-provider, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::billing
- text: The User pays at the billing provider
  kind: actor
  actor: user
  entities:
  - {entity: billing-provider, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::billing
- text: The Product brings the person back to Billing and shows the new plan once the billing provider reports it
  kind: product
  actor: user
  entities:
  - {entity: account, effect: reads, facts: [Plan]}
  - {entity: billing-provider, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::billing
---

# Upgrade to Hobby or Pro

## Trigger

A person needs more links, members, custom domains, QR styling or longer analytics.

## Outcome

The person's plan is the one bought, for every organization they own.
