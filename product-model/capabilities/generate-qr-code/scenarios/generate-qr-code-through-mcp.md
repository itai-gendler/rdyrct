---
kind: alternative
routes:
  mcp: MCP server
steps:
- text: The AI agent asks for a QR code for a web address
  kind: actor
  actor: ai-agent
  entities: []
  contexts:
    mcp:
      place: mcp-server
- text: The Product checks the address is a valid http or https address and returns a PNG of its QR code
  kind: product
  actor: ai-agent
  entities: []
  contexts:
    mcp:
      place: mcp-server
---

# An AI agent makes a QR code

## Trigger

A person asks their AI agent for a QR code.

## Outcome

The AI agent has a PNG image of the QR code.

## Edge cases

- An address that is not a valid http or https address gets an error instead of an image.
