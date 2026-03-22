# Contributing to the AI Agent Compliance Data Model

Thank you for your interest in contributing. This is an open specification — we want it to reflect the real needs of practitioners, not just one vendor's perspective.

## How to Contribute

### Feedback on v0.1

The best way to contribute right now is to open an Issue:

- **Field missing or wrong?** Open an issue describing the gap and your use case.
- **Regulatory mapping incorrect?** Cite the article and describe the correct interpretation.
- **Implementation question?** Ask — we'll clarify and improve the spec based on common questions.
- **Tool integration?** If you're implementing this in your tool, open an issue to let us know. We'll list compatible implementations.

→ [Open an Issue](https://github.com/Veridion-nexus/ai-agent-compliance-spec/issues)

### Proposing Changes

For substantive changes to the data model:

1. Open an Issue first to discuss the change
2. Fork the repo and create a branch: `proposal/your-change-name`
3. Edit the spec in `spec/v0.1.md`
4. Submit a Pull Request referencing the Issue

### What We're Looking For in v0.2

The following areas are explicitly out of scope for v0.1 and candidates for v0.2:

- Consent records and withdrawal events
- DSAR (Data Subject Access Request) workflow events
- Agent-to-agent (A2A) delegation chains and inherited trust
- Cryptographic signing of records
- Retention and deletion schedules per record type
- National DPA reporting format mappings (BfDI, CNIL, ICO, etc.)

If you have requirements in any of these areas, open an Issue tagged `v0.2`.

## Principles

**Minimal by default.** The spec defines the floor, not the ceiling. We prefer fewer required fields that every tool can implement over comprehensive fields that most tools will leave empty.

**Regulatory accuracy over simplicity.** If a field exists to satisfy a specific regulatory obligation, that obligation should be cited. If you think a citation is wrong or missing, say so.

**Complementary, not competing.** This spec is designed to work alongside A2A, MCP, OpenTelemetry, and existing compliance tools — not replace them.

## Code of Conduct

Be direct, be precise, be respectful. This is a technical specification — disagreements should be about the spec, not the people.

## Contact

For questions not suited to a public Issue: compliance-spec@veridion-nexus.eu
