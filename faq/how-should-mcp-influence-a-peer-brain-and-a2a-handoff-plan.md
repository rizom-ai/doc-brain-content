---
question: How should MCP influence a peer-brain and A2A handoff plan?
status: draft
asked: 2
---
# FAQ

## Answer
Keep the handoff explicit and trust-gated. Use MCP as an assistant/tooling interface, but treat peer-brain exchange as a separate A2A path—not an automatic consequence of MCP connectivity. Add peers through the documented discovery flow, review and approve them, and rely on signed peer identity and the approved domain/key binding for calls. Keep ambient discovery disabled until its policy correction is in place.

Sources: **Interface Setup**; **Agent Discovery**.

## Sources

- [Interface Setup](https://docs.rizom.ai/docs/interface-setup "doc:interface-setup")
- [Agent Discovery](https://docs.rizom.ai/docs/agent-discovery "doc:agent-discovery")

## Alternative answers

### Alternative answer 1

#### Answer
Use MCP for a caller’s interaction with its own brain, and A2A for brain-to-brain handoffs. MCP routes clients through the brain agent and filters tools by permission; an MCP connection should not be treated as peer authorization.

For A2A, keep peers as agent contacts with an explicit approval step. Handoffs should verify the peer’s signed identity and approved domain/key binding. The receiving brain should derive the caller’s identity from that verification, not from a role claimed in the request. Keep discovery and approval distinct: finding a peer does not grant permission to call it.

Sources: **Interface Setup** and **Agent Discovery**.
