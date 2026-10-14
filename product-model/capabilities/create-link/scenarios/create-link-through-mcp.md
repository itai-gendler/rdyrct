---
kind: alternative
routes:
  mcp: MCP server
steps:
- text: The AI agent asks to shorten a destination, optionally with a title, a custom domain and a slug, in one of the person's organizations
  kind: actor
  actor: ai-agent
  entities:
  - {entity: organization, effect: reads, facts: []}
  - {entity: custom-domain, effect: reads, facts: []}
  contexts:
    mcp:
      place: mcp-server
- text: The Product resolves the organization, the person's only one unless named, and creates the link exactly as the app would
  kind: product
  actor: ai-agent
  entities:
  - {entity: link, effect: creates, to: Active, facts: [Slug, Domain, Short URL, Destination, Title, Created by, Created, Clicks]}
  - {entity: organization, effect: reads, facts: []}
  contexts:
    mcp:
      place: mcp-server
---

# An AI agent creates a link

## Trigger

A person asks their AI agent to shorten an address.

## Outcome

The AI agent has the new short address.

## Edge cases

- A person in several organizations who names none is asked which one.
