---
kind: alternative
routes:
  link: Short link
steps:
- text: The Visitor opens an anonymous short address made on the home page
  kind: actor
  actor: visitor
  entities: []
  contexts:
    link:
      place: short-links
- text: The 24 hours have not run out
  kind: condition
  actor: visitor
  entities:
  - {entity: anonymous-link, effect: reads, facts: [Expires]}
  contexts:
    link:
      place: short-links
- text: The Product redirects to its destination and adds one to its total, keeping nothing else about the visit
  kind: product
  actor: visitor
  entities:
  - {entity: anonymous-link, effect: changes, facts: [Click total]}
  contexts:
    link:
      place: short-links
---

# Follow an anonymous short address

## Trigger

Someone follows a short address made without an account.

## Outcome

The Visitor lands on the destination and the maker sees the total grow.
