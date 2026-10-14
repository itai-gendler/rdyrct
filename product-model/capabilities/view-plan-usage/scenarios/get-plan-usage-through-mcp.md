---
kind: alternative
routes:
  mcp: MCP server
steps:
- text: The AI agent asks for an organization's plan usage
  kind: actor
  actor: ai-agent
  entities:
  - {entity: organization, effect: reads, facts: []}
  contexts:
    mcp:
      place: mcp-server
- text: The Product returns the plan, how many links it allows, how many are used and how many are left
  kind: product
  actor: ai-agent
  entities:
  - {entity: organization, effect: reads, facts: [Plan]}
  - {entity: link, effect: reads, facts: []}
  contexts:
    mcp:
      place: mcp-server
---

# An AI agent reads plan usage

## Trigger

A person asks their AI agent how many links they have left.

## Outcome

The AI agent has the numbers.
