---
kind: alternative
routes:
  web: Web app
steps:
- text: The Platform admin deletes an organization from the admin console and confirms
  kind: actor
  actor: platform-admin
  entities:
  - {entity: organization, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web::admin-console::organizations
- text: The Product deletes it as the owner would, and records the deletion with the organization's name in the audit log
  kind: product
  actor: platform-admin
  entities:
  - {entity: organization, effect: removes, from: Locked}
  - {entity: link, effect: removes, from: Active, with: organization}
  - {entity: membership, effect: removes, with: organization}
  contexts:
    web:
      place: web::admin-console::organizations
---

# Delete an organization from the admin console

## Trigger

A Platform admin removes an abusive or abandoned organization.

## Outcome

The organization is gone and the audit log says which one.
