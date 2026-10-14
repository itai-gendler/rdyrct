---
appliesTo:
- type: entity
  id: invite
  effect: removes
  contexts:
  - place: web::workspace::invite
- type: entity
  id: membership
  effect: creates
  contexts:
  - place: web::workspace::invite
permits:
- actors:
  - user
references:
- kind: code
  role: implementation
  target: src/worker/routes/orgs.ts#inviteRoutes
---

# An emailed invite is accepted only by the account with that address

Any signed-in person who holds an invite link accepts it; an emailed invite is accepted only by the account whose address it was sent to. Accepting spends the invite.
