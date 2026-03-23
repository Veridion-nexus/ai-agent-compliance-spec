# Contributing to the AI Agent Compliance Data Model

This spec is maintained by [Veridion Nexus](https://veridion-nexus.eu) and designed to be implemented by any tool in the AI agent compliance stack. We're looking for implementers, not just feedback — the most valuable contributions come from people who have tried to build against v0.1 and hit its limits.

---

## How to contribute

**Open a GitHub Issue** for any of the following:
- A field definition that conflicts with a regulatory requirement you've encountered
- A use case the current schema doesn't cover
- An implementation report from a real deployment (what worked, what didn't)
- A proposed addition for v0.2

**Open a Pull Request** for:
- Corrections to field definitions or regulatory citations
- Clarifications to implementation guidance
- New entries in the "Relationship to Existing Standards" table

All substantive changes go through a public Issue before being merged. This keeps the change history transparent and auditable — which is appropriate for a compliance spec.

---

## v0.2 — Open problems we're actively looking for input on

These are the known gaps in v0.1. If you're working in any of these areas, opening an Issue with your use case is exactly the kind of contribution that shapes v0.2.

### 1. Agent-to-agent delegation chains ← highest priority

The current `event_ref` pointer system only links a single ToolCallEvent back to a parent record. It doesn't represent chains: "Orchestrator Agent invoked Research Agent which called a web search tool." In multi-agent systems — which are already in production — this means the audit trail loses provenance at every handoff.

**What we need:** A schema for representing delegation depth, inherited trust levels, and chain-of-custody across agent-to-agent calls. If you're running multi-agent pipelines and have thought about how to represent this for compliance purposes, please open an Issue.

### 2. Retention policy and TTL per record type

v0.1 defines what to log but not how long to keep it. Supervisory authorities will ask. The answer varies by record type (a ToolCallEvent tied to an employment decision has different retention obligations than a DataTransferRecord under SCCs) and by jurisdiction.

**What we need:** Proposed retention rules, ideally grounded in specific DPA guidance or legal analysis.

### 3. Cryptographic signing of records

Without signing, an audit log can be challenged on admissibility grounds in enforcement proceedings. This is particularly relevant for the `HumanOversightRecord` — if a regulator asks whether a human actually reviewed a decision, an unsigned log is weaker evidence than a signed one.

**What we need:** Proposals for a signing scheme that works across different implementing tools without requiring a shared key infrastructure.

### 4. Consent records and withdrawal events

v0.1 covers legitimate interests and SCC-based processing. It has no representation for consent as a legal basis, consent withdrawal, or the downstream effect of withdrawal on existing records.

### 5. DSAR workflow events

When a data subject exercises Art. 15–17 rights against an AI agent's decisions, the current spec has no record type for the request, the response, or the deletion/correction of affected records.

---

## What we don't want

- Field additions that duplicate what existing standards already cover well (use the mapping table and reference the standard instead)
- Breaking changes to v0.1 field names or types — these go through a deprecation cycle
- Jurisdiction-specific fields in the core schema — national extensions belong in a separate annex

---

## Versioning and stability

The [CHANGELOG](./CHANGELOG.md) documents every release. If a regulatory publication conflicts with a current field definition, we issue a versioned update (v0.x) within 30 days and document the conflict in the GitHub Issue thread. We do not silently patch released versions.

---

*AI Agent Compliance Data Model is published under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Contributions are made under the same license.*
