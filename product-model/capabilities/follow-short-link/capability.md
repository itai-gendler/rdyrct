---
availability:
- {place: short-links}
references:
- kind: code
  role: implementation
  target: src/worker/index.ts#redirectWithClick
- kind: code
  role: implementation
  target: src/worker/index.ts#resolveLink
- kind: code
  role: implementation
  target: src/worker/storage.ts#desiredLink
- kind: code
  role: implementation
  target: src/worker/kv.ts#domainServing
- kind: code
  role: implementation
  target: src/worker/clicks.ts#enqueueClick
- kind: code
  role: implementation
  target: src/worker/risk.ts#revalidateOnRedirect
---

# Follow a short link

Following a short address redirects to the link's destination with its UTM parameters, and records the click. It works for every address a link answers to, on the shared domain and on custom domains.
