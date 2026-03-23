# Changelog

All notable changes to the AI Agent Compliance Data Model are documented here.

When a regulatory publication, DPA guidance, or protocol update conflicts with a field definition in the current spec, a versioned update is issued within 30 days. v0.1 is never silently patched. The [GitHub Issues thread](https://github.com/Veridion-nexus/ai-agent-compliance-spec/issues) is the canonical record of known conflicts and proposed changes between releases.

---

## [0.1] — 2026-03-20

Initial draft for public comment.

### Added
- `AgentRecord` — identity and policy profile of a registered AI agent (GDPR Art. 30, EU AI Act Art. 16)
- `ToolCallEvent` — a single tool invocation with data minimization and context trust fields (GDPR Art. 5(1)(c), EU AI Act Art. 14)
- `DataTransferRecord` — cross-border personal data transfer with transfer mechanism tracking (GDPR Chapter V, Arts. 44–49)
- `ContextTrustAnnotation` — trust level of agent context at decision time, compatible with AgentLock v1.1 semantics (EU AI Act Art. 14, GDPR Art. 22)
- `HumanOversightRecord` — human review or override of an agent decision (EU AI Act Art. 14)
- Relationship model: `agent_id` as shared key across all objects; `event_ref`, `annotation_ref`, `oversight_record_ref` for cross-object linking
- Suggested `/.well-known/acm/` endpoint structure for interoperability
- Mappings to GDPR Art. 30, EU AI Act Art. 14, A2A Protocol, MCP, AgentLock v1.1, and OpenTelemetry

### Deliberately deferred to v0.2
- Agent-to-agent (A2A) delegation chains — current `event_ref` pointer system does not scale to multi-agent chains
- Cryptographic signing of records for tamper-evidence
- Retention policy and TTL definitions per record type
- Consent records and withdrawal events
- Data subject access request (DSAR) workflow events
- Mapping to specific national DPA reporting formats

---

*This project follows [Semantic Versioning](https://semver.org/) adapted for specifications: MAJOR = breaking schema change, MINOR = new objects or fields (backwards-compatible), PATCH = clarifications and non-normative corrections.*
