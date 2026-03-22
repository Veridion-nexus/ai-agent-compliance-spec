# AI Agent Compliance Data Model

**Version:** 0.1 — Draft for Public Comment  
**Status:** Draft  
**License:** [CC BY 4.0](LICENSE)  
**Published by:** [Veridion Nexus](https://veridion-nexus.eu)  
**Feedback:** [Open an Issue](https://github.com/Veridion-nexus/ai-agent-compliance-spec/issues)

---

## What This Is

A minimal, interoperable data model for AI agent compliance events.

AI agents make autonomous decisions, call external tools, and transfer data across jurisdictions — often faster than any human oversight loop. The compliance infrastructure around them is fragmented: security tools track what tools were called, IT governance tools track which agents exist, and legal/privacy tools track data flows. None of them share a common data model.

This specification defines five core objects that together satisfy:

- **GDPR Art. 30** — Records of processing activities
- **GDPR Chapter V (Arts. 44–49)** — Cross-border data transfer audit trail  
- **EU AI Act Art. 14** — Human oversight for high-risk AI systems
- **Internal audit requirements** for agentic AI deployments

## The Five Objects

| Object | What it captures |
|--------|-----------------|
| `AgentRecord` | Identity and policy profile of a registered agent |
| `ToolCallEvent` | A single tool invocation by an agent |
| `DataTransferRecord` | A cross-border personal data transfer |
| `ContextTrustAnnotation` | Trust level of agent context at decision time |
| `HumanOversightRecord` | A human review or override of an agent decision |

## Read the Spec

→ **[spec/v0.1.md](spec/v0.1.md)**

## Why an Open Standard

The EU AI Act Annex III enforcement deadline is August 2026. Enterprises deploying AI agents need to produce compliant audit trails — but every tool in the stack (security, governance, compliance) produces different records in different formats.

This spec is designed to be the shared vocabulary. If LangGuard, AgentLock, and Veridion Nexus all emit `DataTransferRecords` in this format, a DPO gets one coherent audit trail instead of three incompatible logs.

## Relationship to Existing Standards

| Standard | Relationship |
|----------|-------------|
| GDPR Art. 30 | `AgentRecord` + `DataTransferRecord` satisfy Art. 30(1) record requirements |
| EU AI Act Art. 14 | `HumanOversightRecord` is a direct implementation artifact |
| Google A2A Protocol | `AgentRecord.a2a_card_url` links to A2A agent card |
| MCP (Anthropic) | `ToolCallEvent` maps to MCP tool call semantics |
| AgentLock v1.1 | `ContextTrustAnnotation` formalises AgentLock's trust level concept |
| OpenTelemetry | Record IDs and timestamps are compatible with OTel trace/span conventions |

## Reference Implementation

[Veridion Nexus](https://veridion-nexus.eu) implements this data model in its runtime GDPR enforcement engine for AI agents. The Evidence Vault produces `DataTransferRecords` and `HumanOversightRecords` compatible with this spec.

## Contributing

This is a draft. We want feedback from:
- Privacy engineers and DPOs implementing AI agent compliance
- Tool builders in the agent security, governance, and observability space
- Regulators and legal practitioners working on AI Act compliance

See [CONTRIBUTING.md](CONTRIBUTING.md) to get involved.

## License

[Creative Commons Attribution 4.0 International (CC BY 4.0)](LICENSE)

Free to implement, adapt, and extend with attribution.
