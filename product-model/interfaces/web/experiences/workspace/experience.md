---
actors:
- user
- platform-admin
access: authenticated
entryPoints:
- web: /dashboard
- web: /invite/:token
---

# Workspace

The signed-in app for the organization currently chosen in the organization switcher. Every signed-in person has one; what they can change depends on the Role their membership holds there. Platform admins pass every organization's role checks as its owner.
