# Contributing to the AI Agent Compliance Data Model

This is a draft specification. v0.1 defines five core objects. We need practitioners to stress-test it against real deployments before v0.2 locks the model.

We're looking for **implementers**, not just feedback.

## Three specific things you can contribute right now

### 1. Implementation reports
Are you building agent governance tooling? Tell us what you're implementing and where the spec doesn't fit. Open an issue tagged `implementation-report` and describe:
- Which objects you're implementing (`AgentRecord`, `ToolCallEvent`, etc.)
- What fields you had to add or drop
- What regulatory requirement drove the gap

Implementation reports directly shape v0.2. If three implementers need the same field, it goes in.

### 2. Field proposals for v0.2
The following areas are explicitly deferred from v0.1 and need real-world input:

- **Consent records** — what does a consent event look like for an agent that processes data on behalf of a user?
- **A2A delegation chains** — when Agent A delegates to Agent B, how do we track inherited trust and accountability?
- **Cryptographic signing** — what's the minimal signing scheme that a DPO would accept as tamper-evident?
- **National DPA reporting formats** — BfDI (Germany), CNIL (France), ICO (UK) all have different Art. 30 record formats. Can this spec map to all three?
- **DSAR workflow events** — what does a data subject access request look like in an agentic system?

Open an issue tagged `v0.2-proposal` with your proposed field, type, and regulatory justification.

### 3. Integration case studies
If you integrate this data model with an existing tool — LangGuard, AgentLock, OpenTelemetry, a SIEM, a DPO portal — open an issue tagged `integration` describing:
- What tool you integrated with
- Which objects you used
- What the integration produced

We'll list confirmed integrations in the README.

## How to propose a change

1. Open an Issue first — describe the problem, not the solution
2. Fork the repo, create a branch: `proposal/your-change-name`
3. Edit `spec/v0.1.md` (or create `spec/v0.2-draft.md` for v0.2 proposals)
4. Submit a Pull Request referencing the Issue

## Principles

**Minimal by default.** The spec defines the floor, not the ceiling. We prefer fewer required fields that every tool can implement over comprehensive fields that most tools will leave empty.

**Regulatory accuracy over simplicity.** If a field exists to satisfy a specific regulatory obligation, that obligation should be cited. If you think a citation is wrong or missing, say so.

**Complementary, not competing.** This spec is designed to work alongside A2A, MCP, OpenTelemetry, and existing compliance tools — not replace them.

## Code of Conduct

Be direct, be precise, be respectful. This is a technical specification — disagreements should be about the spec, not the people.

## Contact

For questions not suited to a public Issue: compliance-spec@veridion-nexus.eu
