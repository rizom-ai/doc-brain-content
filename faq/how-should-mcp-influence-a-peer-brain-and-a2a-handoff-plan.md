---
question: How should MCP influence a peer-brain and A2A handoff plan?
status: draft
asked: 1
---
# FAQ

## Answer
Keep the handoff explicit and trust-gated. Use MCP as an assistant/tooling interface, but treat peer-brain exchange as a separate A2A path—not an automatic consequence of MCP connectivity. Add peers through the documented discovery flow, review and approve them, and rely on signed peer identity and the approved domain/key binding for calls. Keep ambient discovery disabled until its policy correction is in place.

Sources: **Interface Setup**; **Agent Discovery**.

## Sources

- [Interface Setup](https://docs.rizom.ai/docs/interface-setup "doc:interface-setup")
- [Agent Discovery](https://docs.rizom.ai/docs/agent-discovery "doc:agent-discovery")
