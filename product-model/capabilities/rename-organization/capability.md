---
availability:
- {place: 'web::workspace'}
domain: organization
references:
- kind: code
  role: implementation
  target: src/worker/routes/orgs.ts#requireOrgName
- kind: code
  role: implementation
  target: src/app/routes/organization.tsx#OrganizationPage
---

# Rename organization

Change the organization's name on its settings page.
