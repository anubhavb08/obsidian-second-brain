# Implementation Notes

## Working Brand

The working market-facing product name is **Zandem.ai**.

Growth Automation Studio remains the internal architecture and business descriptor. Do not rename architecture files, package metadata, or system identifiers unless the brand is explicitly finalized.

## Separation From Zlicc

Growth Automation Studio is a separate business and product architecture. The Zlicc Growth Console is only a reference implementation for:

- Pre-CRM campaign operations.
- CMO-style agent orchestration.
- Human approval gates.
- Campaign lanes, warm signals, and sales handoff.

No Growth Automation Studio implementation should depend on Zlicc-specific pillars, Zlicc branding, Zlicc offers, Zlicc customers, or Zlicc internal assumptions.

## V1 Product Boundary

V1 is a managed single-client deployment, not a generic multi-tenant SaaS product.

The system should configure a client-specific operating layer around:

- ICPs and offers.
- Brand kit and proof library.
- Campaign lanes.
- AI campaign asset generation.
- Email, LinkedIn, and WhatsApp workflows.
- Warm-signal classification.
- Qualified conversation handoff.
- Scheduled AI CMO review meetings for performance review, decision capture, and action planning.

## Commercial Model

Commercials are intentionally not fixed in this architecture. Pilot pricing, monthly retainers, usage credits, third-party services, and included operational support should be designed later.

## Non-Negotiable Guardrails

- LinkedIn is review, recommendation, and tasking only.
- WhatsApp uses compliant WABA paths only.
- Email must be provider-agnostic and approval-gated.
- Human approval remains mandatory for public content, sensitive claims, client references, pricing, proposals, and campaign activation.
- AI CMO review decisions must be converted into explicit action plans and approval requests before they alter live campaigns, outreach, public assets, pricing, proposals, or handoff rules.
- Every agent output must include source context, confidence, risk level, recommended action, and approval requirement.
