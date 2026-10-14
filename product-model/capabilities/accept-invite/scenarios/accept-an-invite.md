---
kind: primary
routes:
  web: Web app
steps:
- text: The User opens the invite and sees the organization and Role it offers
  kind: actor
  actor: user
  entities:
  - {entity: invite, effect: reads, facts: [Role]}
  - {entity: organization, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web::workspace::invite
- text: The User accepts
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::workspace::invite
- text: The invite is still valid, is for this person's address when it was emailed, they are not already a member, and the organization has a free seat
  kind: condition
  actor: user
  entities:
  - {entity: invite, effect: reads, facts: [Email, Expires]}
  - {entity: organization, effect: reads, facts: [Plan]}
  contexts:
    web:
      place: web::workspace::invite
- text: The Product adds the person with the invite's Role, spends the invite, makes the organization current and opens its dashboard
  kind: product
  actor: user
  entities:
  - {entity: membership, effect: creates, facts: [Role, Joined]}
  - {entity: invite, effect: removes}
  - {entity: organization, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::invite
---

# Accept an invite

## Trigger

Someone receives an invitation to a team.

## Outcome

The person is a member with the invite's Role and lands on the dashboard.
