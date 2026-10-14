---
kind: primary
routes:
  web: Web app
steps:
- text: The User opens Billing
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::workspace::billing
- text: The Product shows the plan, whether it cancels at the period end, and the organization's usage of its link, member and custom domain limits
  kind: product
  actor: user
  entities:
  - {entity: account, effect: reads, facts: [Plan, Cancels at period end, Period end]}
  - {entity: organization, effect: reads, facts: [Over plan]}
  - {entity: link, effect: reads, facts: []}
  - {entity: custom-domain, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::billing
---

# See plan usage

## Trigger

A person checks how close they are to the plan's limits.

## Outcome

The person sees their plan and usage.
