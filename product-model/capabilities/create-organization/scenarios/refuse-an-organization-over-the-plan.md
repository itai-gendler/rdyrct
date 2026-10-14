---
kind: validation
routes:
  web: Web app
steps:
- text: The User creates another organization
  kind: actor
  actor: user
  entities:
  - {entity: organization, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace
- text: The person already owns as many organizations as their plan covers
  kind: condition
  actor: user
  entities:
  - {entity: account, effect: reads, facts: [Plan]}
  - {entity: organization, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace
- text: The Product refuses and points to Pro
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: web::workspace
---

# Refuse an organization over the plan

## Trigger

A Free or Hobby person who owns one organization creates a second.

## Outcome

No organization is created.
