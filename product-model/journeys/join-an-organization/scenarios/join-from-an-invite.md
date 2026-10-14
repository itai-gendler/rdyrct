---
kind: primary
result: achieved
routes:
  web: Web app
steps:
- text: The User opens the invite and accepts it
  kind: actor
  actor: user
  capability: accept-invite
  entities:
  - {entity: invite, effect: reads, facts: [Role]}
  - {entity: organization, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web::workspace::invite
- text: The Product adds the person with the invite's Role and spends the invite
  kind: product
  actor: user
  capability: accept-invite
  entities:
  - {entity: membership, effect: creates, facts: [Role, Joined]}
  - {entity: invite, effect: removes}
  contexts:
    web:
      place: web::workspace::invite
- text: The Product makes the organization current and opens its dashboard
  kind: product
  actor: user
  capability: accept-invite
  entities:
  - {entity: organization, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::invite
- text: The User looks over the dashboard
  kind: actor
  actor: user
  capability: view-dashboard
  entities: []
  contexts:
    web:
      place: web::workspace::dashboard
- text: The Product shows the organization's click totals, latest clicks and latest links
  kind: product
  actor: user
  capability: view-dashboard
  entities:
  - {entity: organization, effect: reads, facts: []}
  - {entity: click, effect: reads, facts: [Time, Country, Referrer, Device]}
  - {entity: link, effect: reads, facts: [Short URL, Title, Created by, Created, Clicks]}
  contexts:
    web:
      place: web::workspace::dashboard
---

# Join from an invite

## Trigger

A person who received an invite opens it while signed in.

## Outcome

The person belongs to the organization and is on its dashboard, with the organization chosen in the switcher.
