---
appliesTo:
- type: entity
  id: link
  effect: creates
permits:
- related:
  - &id001 {verb: has, entity: organization}
  - &id002 {verb: has, entity: membership}
  - &id003 {verb: holds, entity: user}
  when:
  - &id004
    entity: membership
    fact: Role
    is-not: Viewer
- related:
  - *id001
  - *id002
  - *id003
  - {verb: connects, entity: ai-agent}
  when:
  - *id004
- actors:
  - platform-admin
references:
- kind: code
  role: implementation
  target: src/worker/routes/links.ts#linkRoutes
- kind: code
  role: implementation
  target: src/worker/org-role.ts#requireOrgRole
---

# Owners, admins and members create links; viewers do not

Creating a link needs a Role above Viewer in the organization; an AI agent creates links only for a person whose Role allows it. Platform admins act as owner everywhere. Keeping a home-page short address after signing up creates a link the same way.
