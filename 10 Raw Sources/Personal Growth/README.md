# Growth Automation Studio

Standalone business and product architecture for a managed B2B pre-CRM growth system.

Working market-facing product name: **Zandem.ai**.

Growth Automation Studio remains the internal architecture and business descriptor until the brand is finalized.

This workspace is intentionally separate from the Zlicc Growth Console. Zlicc is used only as a reference implementation for the kind of operating model we want to generalize.

## What This Defines

- A 14-agent operating model: 1 Growth CMO Orchestrator plus 13 specialist agents.
- The reporting structure, approval boundaries, and channel guardrails.
- The end-to-end event flow from client onboarding to CRM handoff and weekly optimization.
- A scheduled AI CMO review loop for voice-based performance review, decision capture, and action planning.
- Machine-readable registries for agents, event types, and channel policies.
- A validation script that checks the architecture stays aligned with the agreed plan.

## Files

- [Product Flowcharts](docs/product-flowcharts.md)
- [Infographic Images](docs/infographics/README.md)
- [Onboarding One-Sheet](docs/onboarding-one-sheet.md)
- [Agent Architecture](docs/agent-architecture.md)
- [Event Flow Architecture](docs/event-flow-architecture.md)
- [Overall Plan](docs/overall-plan.md)
- [Tooling Stack](docs/tooling-stack.md)
- [Implementation Notes](docs/implementation-notes.md)
- [Agent Registry](data/agent-registry.json)
- [Event Taxonomy](data/event-taxonomy.json)
- [Tool Stack Registry](data/tool-stack.json)
- [Channel Guardrails](data/channel-guardrails.json)

## Validate

```bash
npm run validate
```
