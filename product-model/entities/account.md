---
references:
- kind: code
  role: implementation
  target: src/worker/db/schema.ts#user
- kind: code
  role: implementation
  target: src/worker/entitlement.ts#resolveEffectivePlan
---

# Account

What the Product keeps about one person, whatever they are doing: who they are, their plan, and whether they may sign in. Billing is per account: one plan per person, and every organization a person owns works within that plan.

## Information kept

- **Name** — the name shown for the person; taken from the email address at sign-up
- **Email** — the address the person signs in with; unique on the instance
- **Picture** — an optional profile picture
- **Email verified** — whether the person confirmed the address with the emailed code
- **Platform admin** — whether the account administers the whole instance
- **Plan** — Free, Hobby or Pro, derived from the comp plan first and then from a subscription whose status keeps access; Unlimited on an instance that sells no plans
- **Subscription plan** — the plan a subscription pays for, as the billing provider reports it
- **Subscription status** — the billing provider's own status for that subscription
- **Cancels at period end** — whether the subscription is set to end when the paid period runs out
- **Period end** — when the current paid period ends
- **Billing account** — whether the billing provider holds a customer record for the person
- **Comp plan** — a paid plan a Platform admin granted by hand
- **Comp reason** — why the comp was granted
- **Comp granted by** — the Platform admin who granted it
- **Comp granted at** — when it was granted
- **Joined** — when the account was created
- **Last seen** — the latest activity of any of the person's sessions

## States

### Active

The person may sign in.

### Banned

A Platform admin banned the account: its sessions ended and it cannot sign in. Its organizations and their links keep working.
