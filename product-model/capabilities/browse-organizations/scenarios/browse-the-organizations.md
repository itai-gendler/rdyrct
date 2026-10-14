---
kind: primary
routes:
  web: Web app
steps:
- text: The Platform admin opens Organizations, searching or sorting the list
  kind: actor
  actor: platform-admin
  entities:
  - {entity: organization, effect: reads, facts: []}
  contexts:
    web:
      place: web::admin-console::organizations
- text: The Product lists every organization with its owner, the owner's plan, and its member, link and click counts
  kind: product
  actor: platform-admin
  entities:
  - {entity: organization, effect: reads, facts: [Name, Plan, Created]}
  - {entity: account, effect: reads, facts: [Name, Email]}
  - {entity: link, effect: reads, facts: []}
  - {entity: click, effect: reads, facts: []}
  contexts:
    web:
      place: web::admin-console::organizations
- text: The Platform admin views one organization
  kind: actor
  actor: platform-admin
  entities:
  - {entity: organization, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web::admin-console::organizations
- text: The Product shows its members with their Roles and whether a downgrade demoted them, its links with clicks, and its clicks over the last 30 days
  kind: product
  actor: platform-admin
  entities:
  - {entity: membership, effect: reads, facts: [Role, Demoted]}
  - {entity: link, effect: reads, facts: [Short URL, Destination, Created, Clicks]}
  - {entity: click, effect: reads, facts: []}
  contexts:
    web:
      place: web::admin-console::organizations
---

# Browse organizations

## Trigger

A Platform admin looks into an organization.

## Outcome

The Platform admin sees who is in it and what it holds.
