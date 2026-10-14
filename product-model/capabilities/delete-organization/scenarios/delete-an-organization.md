---
kind: primary
routes:
  web: Web app
steps:
- text: The User deletes the organization, typing its name to confirm
  kind: actor
  actor: user
  entities:
  - {entity: organization, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web::workspace::organization
- text: The Product stops taking changes for the organization and deletes it with its links, custom domains, members and invites, then disconnects its hostnames, stops its addresses and removes its uploaded logos
  kind: product
  actor: user
  entities:
  - {entity: organization, effect: removes, from: Active}
  - {entity: link, effect: removes, from: Active, with: organization}
  - {entity: custom-domain, effect: removes, from: Active, with: organization}
  - {entity: membership, effect: removes, with: organization}
  - {entity: invite, effect: removes, with: organization}
  contexts:
    web:
      place: web::workspace::organization
---

# Delete the organization

## Trigger

The owner no longer needs the organization.

## Outcome

The organization is gone and the person switches to another one, or sees the create-organization prompt if none is left.
