---
kind: alternative
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
- text: The Product creates the account and signs the person in at once
  kind: product
  actor: visitor
  entities:
  - {entity: account, effect: creates, to: Active, facts: [Name, Email, Email verified, Platform admin, Plan, Joined]}
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

# Sign up on an instance that sends no email

## Trigger

A Visitor signs up on a private instance with no email provider.

## Outcome

The person is signed in with an unconfirmed account and owns one organization.
