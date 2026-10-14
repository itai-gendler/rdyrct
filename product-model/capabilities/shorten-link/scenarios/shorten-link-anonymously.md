---
kind: primary
routes:
  web: Web app
steps:
- text: The Visitor pastes a web address into the home page shortener and submits it
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::home
- text: The Product checks that the address is a valid http or https address and not another URL shortener
  kind: product
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::home
- text: The Product makes a short address with a random slug on the shared domain that expires in 24 hours
  kind: product
  actor: visitor
  entities:
  - {entity: anonymous-link, effect: creates, facts: [Slug, Destination, Expires, Click total]}
  contexts:
    web:
      place: web::public::home
- text: The Product shows the short address, its total so far and when it expires
  kind: product
  actor: visitor
  entities:
  - {entity: anonymous-link, effect: reads, facts: [Slug, Expires, Click total]}
  contexts:
    web:
      place: web::public::home
---

# Shorten an address from the home page

## Trigger

A Visitor wants a short address for a page without signing up.

## Outcome

The Visitor has a short address that redirects for 24 hours, and its click total counts up on the home page.

## Edge cases

- The destination is checked against a security resolver after the response; the check never refuses the address.
- The browser keeps the short address so that signing up later can keep it.
