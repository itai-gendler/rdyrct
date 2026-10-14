---
appliesTo:
- type: entity
  id: link
  effect: creates
- type: entity
  id: alias
  effect: creates
- type: entity
  id: custom-domain
  effect: creates
- type: entity
  id: invite
  effect: creates
- type: entity
  id: membership
  effect: creates
- type: entity
  id: organization
  effect: creates
references:
- kind: code
  role: implementation
  target: src/shared/types.ts#PLAN_LIMITS
- kind: code
  role: implementation
  target: src/worker/plan.ts#orgPlan
- kind: code
  role: implementation
  target: src/worker/plan.ts#countActiveAddresses
- kind: code
  role: implementation
  target: src/worker/routes/orgs.ts#occupiedSeats
- kind: code
  role: implementation
  target: src/worker/plan.ts#setMemberRoleWithinLimit
---

# Every organization works within its owner's plan

An organization has no plan of its own: its limits are its owner's plan. Free allows 1 owned organization, 30 links, 3 members, no custom domain, no QR styling and 7 days of analytics; Hobby 1 organization, 500 links, 5 members, 1 custom domain, QR styling and 30 days; Pro 3 organizations, 3,000 links, 25 members, 5 custom domains, QR styling and 365 days. On an instance that sells no plans, everyone is on Unlimited and nothing is capped. Links count every link's primary address plus every permanent alias; members count people and open invites when inviting and accepting, and people above Viewer when changing Roles.

## Rationale

Billing is per person, so every organization the person owns draws on the one plan they pay for.
