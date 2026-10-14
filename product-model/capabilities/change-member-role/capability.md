---
availability:
- {place: 'web::workspace'}
- {place: rest-api}
domain: members
references:
- kind: code
  role: implementation
  target: src/worker/plan.ts#setMemberRoleWithinLimit
- kind: code
  role: implementation
  target: src/worker/routes/orgs.ts#assertMember
---

# Change member role

Set a member's Role to Admin, Member or Viewer. The owner's Role never changes. Giving write access counts against the plan's member limit; making someone a Viewer is always allowed.
