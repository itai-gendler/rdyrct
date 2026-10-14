---
domain: organization
relations:
- {entity: membership, verb: has, cardinality: one-to-many}
- {entity: invite, verb: has, cardinality: one-to-many}
- {entity: link, verb: has, cardinality: one-to-many}
- {entity: custom-domain, verb: has, cardinality: one-to-many}
references:
- kind: code
  role: implementation
  target: src/worker/db/schema.ts#orgs
- kind: code
  role: implementation
  target: src/worker/db/schema.ts#orgEntitlements
- kind: code
  role: implementation
  target: src/worker/plan.ts#orgPlan
---

# Organization

A team's shared space: its links, custom domains, members and click history. An organization has no plan of its own; it works within its owner's plan.

## Information kept

- **Name** — what the organization is called; named from the owner's email domain when the Product creates it
- **Default domain** — the custom domain new links start on; empty means the shared domain
- **QR defaults** — the logo, pattern, colors, corner style, background, eye color and logo size every new QR code starts from
- **Created** — when the organization was created
- **Plan** — the plan of the organization's owner
- **Over plan** — which of links, members and custom domains exceed the owner's plan, with the count of each
- **Grace period ends** — when custom domains beyond the plan stop serving; empty while nothing is over
- **Links suspended** — whether every link in the organization was suspended at once

## States

### Active

The organization takes changes from its members.

### Locked

The owner holds more organizations than the plan covers and this is one beyond it. It is read-only for everyone, its owner included, and its links keep redirecting.
