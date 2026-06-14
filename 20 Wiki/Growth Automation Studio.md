---
type: wiki
domain: personal_growth
status: active
source_count: 8
last_reviewed: 2026-06-03
---

# Growth Automation Studio

Growth Automation Studio is the internal architecture and business descriptor for the personal-growth product line. `Zandem.ai` was discussed as a possible market-facing name, but it is not finalized.

## Positioning

The product concept is a managed B2B pre-CRM growth system.

It helps clients move from scattered outreach and ad hoc content into a structured operating layer:

Client Brain -> Campaign Lanes -> AI Campaign Assets -> Outreach Workflows -> Warm Signals -> Qualified Conversation Handoff.

Primary source: [[10 Raw Sources/Personal Growth/docs/overall-plan|Growth Automation Studio Overall Plan]]

## Product Modules

- Client Brain.
- Campaign Factory.
- AI Creative Studio.
- Email Integration Layer.
- LinkedIn Review Assistant.
- WhatsApp Layer.
- Warm Signal Layer.
- CRM Handoff.
- AI CMO Review Room.

## Architecture Sources

- [[10 Raw Sources/Personal Growth/docs/agent-architecture|Agent Architecture]]
- [[10 Raw Sources/Personal Growth/docs/event-flow-architecture|Event Flow Architecture]]
- [[10 Raw Sources/Personal Growth/docs/tooling-stack|Tooling Stack]]
- [[10 Raw Sources/Personal Growth/docs/product-flowcharts|Product Flowcharts]]

## Delivery Model

V1 is a managed single-client deployment. The first deployment should produce Client Brain configuration, brand kit, proof library, two to three campaign lanes, AI-generated campaign kits, channel rules, warm-signal logic, CRM handoff, and an AI CMO review rhythm.

## Guardrails

- Keep this separate from [[Zlicc HQ]].
- Do not auto-post, auto-comment, auto-DM, auto-connect, or scrape LinkedIn.
- Do not automate personal WhatsApp.
- Keep public assets, pricing, proposals, outbound messages, and campaign changes approval-gated.
- Treat `Zandem.ai` as a candidate name only until the brand is explicitly finalized.

## Source Snapshots

- [[10 Raw Sources/Personal Growth/README|README]]
- [[10 Raw Sources/Personal Growth/docs/overall-plan|Overall Plan]]
- [[10 Raw Sources/Personal Growth/docs/implementation-notes|Implementation Notes]]
- [[10 Raw Sources/Personal Growth/docs/onboarding-one-sheet|Onboarding One-Sheet]]
- [[10 Raw Sources/Personal Growth/docs/infographics/README|Infographic Images]]

## Open Loops

- Decide commercial model and pricing later.
- Decide final brand identity and name.
- Build a demo flow from onboarding to AI CMO review.
- Decide the first customer segment to validate.
- Create a source-backed feature map from the event taxonomy and agent registry in the source repo.
