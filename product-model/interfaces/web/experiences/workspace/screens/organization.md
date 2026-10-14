---
entities:
- {entity: organization, shows: [Name, QR defaults], collects: [Name, QR defaults]}
entryPoints:
- web: /organization
references:
- kind: code
  role: implementation
  target: src/app/routes/organization.tsx#OrganizationPage
---

# Organization

Settings of the current organization: its name, its QR defaults, and deleting it.
