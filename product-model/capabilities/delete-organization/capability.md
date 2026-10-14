---
availability:
- {place: 'web::workspace'}
- {place: 'web::admin-console'}
references:
- kind: code
  role: implementation
  target: src/worker/routes/orgs.ts#deleteOrgs
- kind: code
  role: implementation
  target: src/worker/workflows.ts#OrgDeleteWorkflow
- kind: code
  role: implementation
  target: src/worker/routes/orgs.ts#sweepStalledOrgDeletions
- kind: code
  role: implementation
  target: src/worker/routes/admin.ts#adminRoutes
---

# Delete organization

Delete an organization with every link, custom domain, member, invite and its click history. Short links stop working immediately and nothing can be recovered. A locked organization can still be deleted. Platform admins delete any organization from the admin console.
