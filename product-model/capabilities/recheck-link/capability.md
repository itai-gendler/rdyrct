---
availability:
- {place: 'web::admin-console'}
domain: platform-links
references:
- kind: code
  role: implementation
  target: src/worker/routes/admin-links.ts#adminLinkRoutes
- kind: code
  role: implementation
  target: src/worker/risk.ts#scoreDestination
---

# Re-check link destination

Run the destination security check again now and see the answer. A provider that does not answer leaves the link unscored, never clean.
