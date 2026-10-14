---
kind: primary
routes:
  web: Web app
steps:
- text: The Platform admin opens the audit log, searching if needed
  kind: actor
  actor: platform-admin
  entities: []
  contexts:
    web:
      place: web::admin-console::audit-log
- text: The Product lists the latest 200 audit entries with who acted, what was done, to what, the detail and when
  kind: product
  actor: platform-admin
  entities:
  - {entity: audit-entry, effect: reads, facts: [Who, Action, Target, Detail, When]}
  contexts:
    web:
      place: web::admin-console::audit-log
---

# Read the audit log

## Trigger

A Platform admin reconstructs who did what to a link, organization or account.

## Outcome

The Platform admin sees the history, even for targets that no longer exist.
