---
kind: alternative
routes:
  mcp: MCP server
steps:
- text: The AI agent asks to invite an email address, as a Member unless it names another Role
  kind: actor
  actor: ai-agent
  entities:
  - {entity: invite, effect: reads, facts: []}
  contexts:
    mcp:
      place: mcp-server
- text: The Product creates and emails the invite exactly as the app would
  kind: product
  actor: ai-agent
  entities:
  - {entity: invite, effect: creates, facts: [Role, Email, Invite link, Created, Expires]}
  contexts:
    mcp:
      place: mcp-server
---

# An AI agent invites someone

## Trigger

A person asks their AI agent to invite a colleague.

## Outcome

The colleague has an invitation email.
