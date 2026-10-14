---
entities:
- {entity: link, shows: [Short URL, Destination, Created by, Created, Clicks, Risk score, Risk reasons, Risk checked, Suspension reason], collects: [Suspension reason]}
- {entity: organization, shows: [Name]}
- {entity: anonymous-link, shows: [Slug, Destination, Expires, Risk score]}
entryPoints:
- web: /admin/links
references:
- kind: code
  role: implementation
  target: src/app/routes/admin/links.tsx
- kind: code
  role: implementation
  target: src/worker/routes/admin-links.ts#adminLinkRoutes
---

# All links

Link moderation across every organization: search by slug or destination, narrow to one organization or to suspended links, sort by newest, clicks or risk, and a separate list of anonymous links.
