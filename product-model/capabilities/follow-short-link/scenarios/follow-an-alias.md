---
kind: alternative
routes:
  link: Short link
steps:
- text: The Visitor opens an alias address of a link
  kind: actor
  actor: visitor
  entities:
  - {entity: link, effect: reads, facts: []}
  - {entity: alias, effect: reads, facts: []}
  contexts:
    link:
      place: short-links
- text: The alias is permanent, or temporary and not yet expired
  kind: condition
  actor: visitor
  entities:
  - {entity: alias, effect: reads, facts: [Slug, Expires]}
  contexts:
    link:
      place: short-links
- text: The Product redirects to the link's destination with its UTM parameters
  kind: product
  actor: visitor
  entities:
  - {entity: link, effect: reads, facts: [Destination, UTM parameters]}
  contexts:
    link:
      place: short-links
- text: After the redirect the Product records the click against the alias
  kind: product
  actor: visitor
  entities:
  - {entity: click, effect: creates, facts: [Time, Country, Referrer, Device, Address]}
  - {entity: alias, effect: reads, facts: []}
  contexts:
    link:
      place: short-links
---

# Follow an alias

## Trigger

Someone follows an older or extra address of a link.

## Outcome

The Visitor lands on the same destination, and the click counts for the link and for the alias.
