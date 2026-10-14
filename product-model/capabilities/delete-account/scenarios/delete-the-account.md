---
kind: primary
routes:
  web: Web app
steps:
- text: The User reads which owned organizations go with the account and confirms
  kind: actor
  actor: user
  entities:
  - {entity: organization, effect: reads, facts: [Name]}
  - {entity: account, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::settings
- text: The Product deletes the account, its API keys and connected apps, and every organization it owns with their links, custom domains, members and click history; the person leaves every other organization they were in
  kind: product
  actor: user
  entities:
  - {entity: account, effect: removes, from: Active}
  - {entity: api-key, effect: removes, from: Active}
  - {entity: connected-app, effect: removes}
  - {entity: organization, effect: removes, from: Active}
  - {entity: link, effect: removes, from: Active, with: organization}
  - {entity: custom-domain, effect: removes, from: Active, with: organization}
  - {entity: membership, effect: removes, with: organization}
  - {entity: click, effect: removes, with: link}
  contexts:
    web:
      place: web::workspace::settings
- text: The Product signs the person out and opens the home page
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: web::workspace::settings
---

# Delete the account

## Trigger

A person leaves the service.

## Outcome

The account and everything it owned are gone; short links of those organizations stop working.
