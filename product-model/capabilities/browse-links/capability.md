---
availability:
- {place: 'web::workspace'}
- {place: rest-api}
- {place: mcp-server}
domain: links
references:
- kind: code
  role: implementation
  target: src/worker/links-page.ts
- kind: code
  role: implementation
  target: src/app/routes/links.tsx#LinksPage
- kind: code
  role: implementation
  target: src/worker/routes/mcp.ts#listLinksTool
---

# Browse links

See an organization's links with their click counts, searched by slug, destination or title, filtered by domain, sorted and paged.
