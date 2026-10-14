---
kind: primary
routes:
  web: Web app
steps:
- text: The Visitor enters an email address and a password and submits
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::sign-up
- text: The Product checks the email domain can receive mail and creates the account, unconfirmed
  kind: product
  actor: visitor
  entities:
  - {entity: account, effect: creates, to: Active, facts: [Name, Email, Email verified, Platform admin, Plan, Joined]}
  contexts:
    web:
      place: web::public::sign-up
- text: The Product emails a six-digit code that lasts 10 minutes
  kind: product
  actor: visitor
  entities:
  - {entity: account, effect: reads, facts: [Email]}
  contexts:
    web:
      place: web::public::sign-up
- text: The Visitor enters the code
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::sign-up
- text: The Product marks the address confirmed and signs the person in
  kind: product
  actor: visitor
  entities:
  - {entity: account, effect: changes, facts: [Email verified]}
  contexts:
    web:
      place: web::public::sign-up
- text: On the first session the Product creates an organization named from the email domain, with the person as its owner
  kind: product
  actor: visitor
  entities:
  - {entity: organization, effect: creates, to: Active, facts: [Name, Created]}
  - {entity: membership, effect: creates, facts: [Role, Joined], with: organization}
  contexts:
    web:
      place: web::public::sign-up
---

# Sign up and confirm the address with a code

## Trigger

A Visitor wants an account on an instance that sends email.

## Outcome

The person is signed in with a confirmed account and owns one organization; the Product takes them on to the page they were going to, the dashboard by default.

## Edge cases

- The account matching the instance's configured admin address is created as a Platform admin.
- A new code can be sent from the code step.
