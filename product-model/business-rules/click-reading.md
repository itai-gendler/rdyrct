---
appliesTo:
- type: entity
  id: click
  effect: reads
permits:
- related:
  - &id001 {verb: has, entity: link}
  - &id002 {verb: has, entity: organization}
  - &id003 {verb: has, entity: membership}
  - &id004 {verb: holds, entity: user}
- related:
  - *id001
  - *id002
  - *id003
  - *id004
  - {verb: connects, entity: ai-agent}
- actors:
  - platform-admin
references:
- kind: code
  role: implementation
  target: src/worker/routes/orgs.ts#orgRoutes
---

# Only an organization's members see its clicks

Click analytics belong to the organization: every member reads them, Viewers included, and so do AI agents a member connected. Platform admins see every organization's clicks.
