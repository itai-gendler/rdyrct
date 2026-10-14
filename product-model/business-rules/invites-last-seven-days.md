---
appliesTo:
- type: entity
  id: invite
  effect: creates
- type: entity
  id: invite
  effect: removes
references:
- kind: code
  role: implementation
  target: src/worker/plan.ts#acceptInviteAtomically
---

# An invite is single-use and lasts seven days

Accepting spends it; one an organization was too full for, or one opened by someone already in the organization, stays usable.
