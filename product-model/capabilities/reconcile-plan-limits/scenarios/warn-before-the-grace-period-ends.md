---
kind: edge
routes:
  web: Web app
steps:
- text: An organization's grace period ends within seven days and the warning has not gone out
  kind: condition
  unattended: true
  entities:
  - {entity: organization, effect: reads, facts: [Grace period ends, Over plan]}
  contexts:
    web:
      place: web::workspace
- text: The Product emails the owner that the organization is over its plan and when its custom domains stop
  kind: product
  entities:
  - {entity: organization, effect: reads, facts: [Name, Over plan, Grace period ends]}
  - {entity: account, effect: reads, facts: [Email]}
  - {entity: custom-domain, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace
---

# Warn a week before custom domains stop

## Trigger

The daily check finds a grace period nearly over.

## Outcome

The owner has a warning; a first notice that failed to send is retried the same way.
