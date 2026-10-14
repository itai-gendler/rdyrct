---
availability:
- {place: 'web::workspace'}
domain: links
references:
- kind: code
  role: implementation
  target: src/worker/routes/links.ts#keepAddressForever
- kind: code
  role: implementation
  target: src/worker/plan.ts#keepAddressForeverWithinLimit
---

# Keep alias forever

Turn a temporary alias a rename left behind into a permanent one, so it never expires. It then counts toward the plan's link limit.
