---
type: wiki
domain: zlicc
status: active
source_count: 2
last_reviewed: 2026-06-03
---

# Zlicc Growth Console Decisions

This page tracks decisions needed to move [[Zlicc Growth Console]] from strategy into implementation.

## Current Product Boundary

Growth Console is a pre-CRM growth layer. Bigin remains the lifecycle CRM in V1.

Growth Console owns prospecting, campaign planning, content, outreach, warm-signal intelligence, approvals, analytics, and qualified lead handoff.

Source: [[10 Raw Sources/Zlicc Marketing/Zlicc_Growth_Console_V1_PRD|Zlicc Growth Console V1 PRD]]

## Open Decisions

- First three campaign lanes after launch.
- Landing page domain and hosting pattern.
- WhatsApp Business API provider.
- SendGrid versus another email platform.
- Apollo plan and API access level.
- Whether Bigin export is manual CSV in V1 or one-click handoff.
- Which internal users and roles are needed for alpha.
- Which proof assets are approved for campaign use.
- Which approval queue states are mandatory for V1.

## Stable Decisions

- LinkedIn stays human-led.
- Personal WhatsApp stays manual.
- Public content requires human approval.
- Pricing, proposals, client references, and high-value prospect actions require approval.
- SendGrid or equivalent handles campaign email sending; Outlook handles reply intelligence.
- WhatsApp automation uses WhatsApp Business API only.

## Suggested Alpha Sequence

1. Product foundation: auth, roles, navigation, growth data core.
2. Manual capture and source identity.
3. CMO Brain recommendations and approval queue.
4. Campaign portfolio with three active lanes.
5. Content Studio and landing page builder.
6. LinkedIn human-in-loop workspace.
7. Reply intelligence and warm-signal tracking.
8. Proof Vault Lite and analytics.

## Link To Operating System

Use [[Zlicc Operating Layer]] for strategic rhythm and [[Zlicc Campaign Focus]] for active lanes. Use this page only for implementation and product decisions.
