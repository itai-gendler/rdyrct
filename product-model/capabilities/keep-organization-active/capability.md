---
availability:
- {place: 'web::workspace'}
references:
- kind: code
  role: implementation
  target: src/worker/plan.ts#keepOrgActive
- kind: code
  role: implementation
  target: src/app/components/over-limit.tsx#OverLimitBanner
---

# Keep organization active

An owner who holds more organizations than the plan covers picks which one stays active. The pick can be swapped back at any time.
