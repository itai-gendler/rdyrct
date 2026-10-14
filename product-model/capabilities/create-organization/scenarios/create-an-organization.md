---
kind: primary
routes:
  web: Web app
steps:
- text: The User chooses New organization and enters a name
  kind: actor
  actor: user
  entities:
  - {entity: organization, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace
- text: The person owns fewer organizations than their plan covers
  kind: condition
  actor: user
  entities:
  - {entity: account, effect: reads, facts: [Plan]}
  - {entity: organization, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace
- text: The Product creates the organization with the person as owner and switches to it
  kind: product
  actor: user
  entities:
  - {entity: organization, effect: creates, to: Active, facts: [Name, Created]}
  - {entity: membership, effect: creates, facts: [Role, Joined], with: organization}
  contexts:
    web:
      place: web::workspace
---

# Create an organization

## Trigger

A person wants a separate space for another team or client.

## Outcome

The new organization is current and empty.
