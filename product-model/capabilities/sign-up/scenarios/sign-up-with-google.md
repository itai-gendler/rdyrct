---
kind: alternative
routes:
  web: Web app
steps:
- text: The Visitor chooses to continue with Google and approves at Google
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::sign-up
- text: The Product creates the account from the Google profile, or connects Google to the existing account with that address, and signs the person in
  kind: product
  actor: visitor
  entities:
  - {entity: account, effect: creates, to: Active, facts: [Name, Email, Email verified, Picture, Platform admin, Plan, Joined]}
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

# Continue with Google

## Trigger

A Visitor prefers their Google identity; offered only where the instance has Google sign-in configured.

## Outcome

The person is signed in and owns one organization.
