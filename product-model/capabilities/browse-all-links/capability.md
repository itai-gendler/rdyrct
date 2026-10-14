---
availability:
- {place: 'web::admin-console'}
domain: platform-links
references:
- kind: code
  role: implementation
  target: src/worker/routes/admin-links.ts#adminLinkFilters
- kind: code
  role: implementation
  target: src/app/routes/admin/links.tsx
---

# Browse all links

Find links across every organization by slug or destination, narrow to one organization or to suspended links, and sort by newest, clicks or risk, with unchecked destinations last. Anonymous links from the home page have their own list.
