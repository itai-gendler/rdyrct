---
appliesTo:
- type: entity
  id: organization
  effect: changes
  facts: [Links suspended]
permits:
- unattended: true
- actors:
  - platform-admin
references:
- kind: code
  role: implementation
  target: src/worker/abuse.ts#sweepAbusiveOrgs
---

# Only the abuse control and platform admins suspend a whole organization's links

Suspending every link of an organization at once is the Product's automatic response to a new free organization flooding the redirect path; a Platform admin can suspend or lift it for a whole organization too.
