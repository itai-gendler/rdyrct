---
appliesTo:
- type: entity
  id: link
  effect: changes
  facts: [Destination, Title, UTM parameters, QR style, Slug, Short URL]
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
---

# Owners, admins and members edit any link of their organization

Editing is not limited to the link's creator: anyone with a Role above Viewer edits every link of the organization, and so does an AI agent acting for them.
