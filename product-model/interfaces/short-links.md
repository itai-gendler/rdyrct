---
type: web
actors:
- visitor
entryPoints:
- web: https://<shared host>/<slug>
- web: https://<custom domain>/<slug>
references:
- kind: code
  role: implementation
  target: src/worker/index.ts#resolveLink
- kind: code
  role: implementation
  target: src/worker/kv.ts#resolveSlug
---

# Short links

The redirect addresses themselves: a slug on the shared host (and the optional second, shorter shared host), or a slug on an organization's custom domain. They answer with a redirect or a not-found page and nothing else; custom domains and the second shared host serve no app pages.
