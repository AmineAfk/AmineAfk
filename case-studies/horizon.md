# Horizon — AI operations platform

[Back to profile](../README.md)

**Focus:** LLM tool integration, ERP inventory data, SQL Server, source grounding, numeric verification and controlled read-only access.

## Problem

Operational questions need current inventory data and an answer that can be traced to its source. A fluent answer alone is insufficient when the requested information is missing or unsupported.

## Implemented approach

The chat application uses a bounded LLM tool loop to call registered business tools. A protected bridge connects those tools to an on-premises ERP database through allowlisted, parameterised, read-only SQL operations. The model selects tools rather than executing arbitrary generated SQL.

The response includes typed source and freshness metadata. Numeric grounding checks prevent unsupported figures from reaching a successful answer; unsupported questions receive an explicit refusal. Server-Sent Events carry progress and the final outcome to the interface.

## My contribution

- Developed the React/Next.js chat interface and streaming API flow.
- Implemented bounded tool execution, registered-tool dispatch and typed result envelopes.
- Implemented source/freshness metadata and deterministic numeric grounding checks.
- Contributed bridge hardening and regression tests for request timeouts, loopback trust and bounded signing-key retrieval.
- Ran end-to-end validation covering product search followed by stock lookup against the connected ERP system.

Horizon is collaborative work. The bridge and business tools also include contributions from another developer.

## Validation

The recorded validation snapshot from **10 October 2026** reports **393 passing tests across 36 test files**, plus lint, type checking, a production build and a client-bundle check. This is a project-wide suite, not a claim that I authored every test or a current uptime measure.

The live validation exercised the model, tools, protected bridge and ERP database. It also checked refusal when requested information was unsupported.

## Design trade-off and current scope

Restricting access to vetted business tools limits the breadth of questions, but makes data access and answer verification easier to reason about. The current integration focuses on read-only operational queries. Employee authentication and further deployment work remain separate milestones; the project is described here as a validated prototype.
