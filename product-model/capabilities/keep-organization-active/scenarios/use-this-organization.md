---
kind: primary
routes:
  web: Web app
steps:
- text: The User chooses Use this one on a locked organization they own
  kind: actor
  actor: user
  entities:
  - {entity: organization, as: kept, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web::workspace
- text: The Product unlocks it and locks the newest of the owner's other active organizations, so the count stays within the plan
  kind: product
  actor: user
  entities:
  - {entity: organization, as: kept, effect: changes, from: Locked, to: Active, facts: []}
  - {entity: organization, as: given-up, effect: changes, from: Active, to: Locked, facts: []}
  contexts:
    web:
      place: web::workspace
---

# Use a locked organization instead

## Trigger

After a downgrade the owner wants a different organization to be the working one.

## Outcome

The chosen organization takes changes again; the other one is read-only and its links keep redirecting.
