---
availability:
- {place: 'web::workspace'}
references:
- kind: code
  role: implementation
  target: src/worker/reconcile.ts#reconcileUser
- kind: code
  role: implementation
  target: src/worker/reconcile.ts#sweepGraceWarnings
- kind: code
  role: implementation
  target: src/shared/types.ts#GRACE_PERIOD_MS
- kind: code
  role: implementation
  target: src/app/components/over-limit.tsx#OverLimitBanner
---

# Apply a plan change to owned organizations

Whenever a person's plan changes, the Product checks every organization they own against the new plan. Nothing is deleted: organizations beyond the plan become read-only, members beyond it become Viewers, custom domains beyond it keep serving for a 30-day grace period and then stop, and over-limit links stay but no new ones can be made. An upgrade puts everything back. The owner is emailed when this starts and again a week before the grace period ends.
