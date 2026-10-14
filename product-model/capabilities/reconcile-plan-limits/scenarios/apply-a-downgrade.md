---
kind: primary
routes:
  web: Web app
steps:
- text: A person's plan went down and their organizations hold more than the new plan allows
  kind: condition
  unattended: true
  entities:
  - {entity: account, effect: reads, facts: [Plan]}
  - {entity: organization, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace
- text: The Product locks the newest organizations beyond the plan's organization limit, keeping the longest-standing ones active
  kind: product
  entities:
  - {entity: organization, effect: changes, from: Active, to: Locked, facts: []}
  contexts:
    web:
      place: web::workspace
- text: In each owned organization it makes the most recently joined members beyond the member limit Viewers, keeping the owner, and locks the newest custom domains beyond the domain limit
  kind: product
  entities:
  - {entity: membership, effect: changes, facts: [Role, Demoted]}
  - {entity: custom-domain, effect: changes, facts: [Locked]}
  - {entity: organization, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace
- text: It records what is over the plan, starts a 30-day grace period, and emails the owner what changed
  kind: product
  entities:
  - {entity: organization, effect: changes, facts: [Over plan, Grace period ends]}
  - {entity: account, effect: reads, facts: [Email]}
  contexts:
    web:
      place: web::workspace
---

# Apply a downgrade

## Trigger

A subscription ended, changed down, or a comp was revoked.

## Outcome

The owner keeps everything they had; the organization shows what is over the plan and until when its custom domains serve.
