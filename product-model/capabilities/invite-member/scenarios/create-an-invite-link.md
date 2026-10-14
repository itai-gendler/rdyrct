---
kind: alternative
routes:
  web: Web app
steps:
- text: The User chooses a Role and creates a shareable invite
  kind: actor
  actor: user
  entities:
  - {entity: invite, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::members
- text: The Product creates a single-use invite for no particular address and copies its address to the clipboard
  kind: product
  actor: user
  entities:
  - {entity: invite, effect: creates, facts: [Role, Invite link, Created, Expires]}
  contexts:
    web:
      place: web::workspace::members
---

# Create an invite link to share

## Trigger

An admin wants to share an invitation in a chat.

## Outcome

The admin has an address that lets one person join within seven days.
