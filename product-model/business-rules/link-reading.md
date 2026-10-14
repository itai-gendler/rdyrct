---
appliesTo:
- type: entity
  id: link
  effect: reads
  facts: [Title, QR style, Created by, Created, Clicks]
permits:
- related:
  - &id001 {verb: has, entity: organization}
  - &id002 {verb: has, entity: membership}
  - &id003 {verb: holds, entity: user}
- related:
  - *id001
  - *id002
  - *id003
  - {verb: connects, entity: ai-agent}
- actors:
  - platform-admin
references:
- kind: code
  role: implementation
  target: src/worker/org-role.ts#requireOrgRole
- kind: code
  role: implementation
  target: src/worker/routes/links.ts#linkRoutes
---

# Only an organization's members see its links' details

Every member of the organization, Viewers included, sees its links' titles, QR styles, clicks and who made them, and so do AI agents a member connected. Platform admins see every link. Following a short address reaches only its destination.
