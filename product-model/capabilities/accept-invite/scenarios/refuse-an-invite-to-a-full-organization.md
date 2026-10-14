---
kind: edge
routes:
  web: Web app
steps:
- text: The User accepts an invite
  kind: actor
  actor: user
  entities:
  - {entity: invite, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::invite
- text: The organization has no free seat on its plan, or the person already belongs to it
  kind: condition
  actor: user
  entities:
  - {entity: organization, effect: reads, facts: [Plan]}
  contexts:
    web:
      place: web::workspace::invite
- text: The Product refuses, says why, and leaves the invite usable
  kind: product
  actor: user
  entities:
  - {entity: invite, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::invite
---

# An invite to a full organization

## Trigger

A team fills up before an invite is used.

## Outcome

Nothing changes; the invite works once a seat frees up.
