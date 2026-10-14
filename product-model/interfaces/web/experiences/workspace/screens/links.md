---
entities:
- {entity: link, shows: [Short URL, Slug, Domain, Destination, Title, UTM parameters, QR style, Clicks, Created, Created by], collects: [Destination, Title, Domain, Slug, UTM parameters, QR style]}
- {entity: alias, shows: [Short URL, Slug, Origin, Expires, Recent clicks, Last use, Top referrers], collects: [Slug]}
- {entity: organization, shows: [Default domain, QR defaults]}
entryPoints:
- web: /links
references:
- kind: code
  role: implementation
  target: src/app/routes/links.tsx#LinksPage
- kind: code
  role: implementation
  target: src/app/components/link-editor.tsx
---

# Links

Every link in the organization, searched, filtered by domain, sorted and paged, with each link's aliases, QR code, editor and actions.
