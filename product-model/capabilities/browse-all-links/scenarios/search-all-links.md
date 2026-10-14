---
kind: primary
routes:
  web: Web app
steps:
- text: The Platform admin searches by a slug or a piece of a destination from an abuse report, optionally narrowing to an organization or to suspended links
  kind: actor
  actor: platform-admin
  entities:
  - {entity: organization, effect: reads, facts: []}
  - {entity: link, effect: reads, facts: []}
  contexts:
    web:
      place: web::admin-console::all-links
- text: The Product lists up to 200 matching links with their organization, clicks, risk score and reasons, and suspension
  kind: product
  actor: platform-admin
  entities:
  - {entity: link, effect: reads, facts: [Short URL, Destination, Created by, Created, Clicks, Risk score, Risk reasons, Risk checked, Suspension reason]}
  - {entity: organization, effect: reads, facts: [Name]}
  - {entity: click, effect: reads, facts: []}
  contexts:
    web:
      place: web::admin-console::all-links
---

# Search links across organizations

## Trigger

A Platform admin answers an abuse report.

## Outcome

The Platform admin finds the reported link.
