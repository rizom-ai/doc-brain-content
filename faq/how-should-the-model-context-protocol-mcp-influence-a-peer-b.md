---
question: >-
  How should the Model Context Protocol (MCP) influence a peer-brain and A2A
  handoff plan, particularly for interoperability and handoff context?
status: draft
asked: 1
---
# FAQ

## Answer
Treat MCP and A2A as complementary interfaces: MCP lets an assistant use a brain’s tools, while A2A lets brains communicate. Keep the handoff at the A2A boundary and pass a concise question with the context needed to answer it. Return the peer’s answer with its sources attributed to that peer; don’t assume MCP tool or session context transfers automatically.

In our plan, `network_ask` selects suitable approved peers, asks them in parallel for brief answers from their public content, and returns answers with citations. Keep outbound approval distinct from inbound trust; trusted A2A calls are authenticated separately.

Sources: **Interface Setup** (MCP and A2A roles, trust, and `network_ask` behavior); **MCP Inspector Guide** (MCP’s assistant/tooling interface and request flow); and the [MCP introduction](https://modelcontextprotocol.io/introduction).

## Sources

- [Interface Setup](https://docs.rizom.ai/docs/interface-setup "doc:interface-setup")
- [MCP Inspector Guide](https://docs.rizom.ai/docs/mcp-inspector-guide "doc:mcp-inspector-guide")
