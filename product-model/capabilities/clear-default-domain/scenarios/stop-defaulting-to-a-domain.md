---
kind: primary
routes:
  web: Web app
steps:
- text: The User chooses to stop defaulting to the current default custom domain
  kind: actor
  actor: user
  entities:
  - {entity: organization, effect: reads, facts: [Default domain]}
  - {entity: custom-domain, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::domains
- text: The Product clears the organization's default domain
  kind: product
  actor: user
  entities:
  - {entity: organization, effect: changes, facts: [Default domain]}
  contexts:
    web:
      place: web::workspace::domains
---

# Stop defaulting to a custom domain

## Trigger

An admin wants new links on the shared domain again.

## Outcome

New links start on the shared domain.

## Edge cases

- Deleting the default custom domain clears the default too.
