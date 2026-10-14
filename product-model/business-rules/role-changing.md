---
appliesTo:
- type: entity
  id: membership
  effect: changes
  facts: [Role]
permits:
- related:
  - {verb: has, entity: organization}
  - {verb: has, entity: membership}
  - {verb: holds, entity: user}
  when:
  - entity: membership
    fact: Role
    is-not: Viewer
  - entity: membership
    fact: Role
    is-not: Member
  - fact: Role
    is-not: Owner
- actors:
  - platform-admin
  when:
  - fact: Role
    is-not: Owner
- unattended: true
references:
- kind: code
  role: implementation
  target: src/worker/routes/orgs.ts#assertMember
- kind: code
  role: implementation
  target: src/worker/reconcile.ts#reconcileUser
---

# Only owners and admins change Roles, and never the owner's

An owner or admin sets anyone but the owner to Admin, Member or Viewer. A plan change demotes and restores members on its own.
