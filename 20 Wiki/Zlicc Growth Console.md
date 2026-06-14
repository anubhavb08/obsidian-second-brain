---
type: wiki
domain: zlicc
status: active
source_count: 5
last_reviewed: 2026-06-03
---

# Zlicc Growth Console

Zlicc Growth Console is the pre-CRM growth engine for [[Zlicc HQ]].

Use [[Zlicc Growth Console Decisions]] for implementation and product decisions. Use [[Zlicc Operating Layer]] for the broader weekly marketing rhythm.

## Product Intent

The Growth Console owns upstream growth work:

- Find the right audiences.
- Turn Zlicc pillars into sellable offers.
- Build campaign lanes.
- Generate and approve content.
- Manage LinkedIn-assisted prospecting.
- Run compliant email and WhatsApp workflows.
- Capture replies and warm signals.
- Score leads and recommend next actions.
- Hand qualified leads into sales and CRM workflows.

Primary source: [[10 Raw Sources/Zlicc Marketing/Zlicc_Growth_Console_V1_PRD|Zlicc Growth Console V1 PRD]]

## Architecture

The system is designed around this operating loop:

Discover lead -> enrich contact -> classify and score -> choose Zlicc offer -> create content and outreach -> quality check -> human approval -> execute -> measure -> improve.

Primary architecture source: [[10 Raw Sources/Zlicc Marketing/Zlicc_Growth_Console_Architecture|Zlicc Growth Console Architecture]]

## V1 Modules

- Growth data core.
- Manual quick capture.
- LinkedIn operator workspace.
- Apollo prospect search and enrichment.
- CMO Brain service.
- Specialist agent operations.
- Seasonal opportunity calendar.
- Campaign portfolio with limited active lanes.
- Landing page builder.
- Content studio.
- Creative production desk.
- WhatsApp Business API assistant.
- Email platform and Outlook reply intelligence.
- Warm signal scoring.
- Proof Vault Lite.
- Analytics and weekly CMO report.

## Human Approval Boundaries

The system should not automatically publish, send sensitive communication, use client references, make pricing promises, or commit delivery timelines without human approval.

Related page: [[Decisions And Guardrails]]

## Source Snapshots

- [[10 Raw Sources/Zlicc Marketing/Zlicc_Growth_Console_V1_PRD|PRD]]
- [[10 Raw Sources/Zlicc Marketing/Zlicc_Growth_Console_Architecture|Architecture]]
- [[10 Raw Sources/Zlicc Marketing/Zlicc_Growth_Console_Engineering_Backlog|Engineering Backlog]]
- [[10 Raw Sources/Zlicc Marketing/Zlicc_Growth_Console_UI_Mockup_Direction|UI Mockup Direction]]
- [[10 Raw Sources/Zlicc Marketing/Zlicc_Growth_Console_Low_Fidelity_Wireframes|Low Fidelity Wireframes]]

## Open Loops

- Decide the immediate alpha scope in [[Zlicc Growth Console Decisions]].
- Confirm the first three campaign lanes.
- Prioritize integrations: Apollo, SendGrid or equivalent, Outlook/Graph, WhatsApp Business API, Bigin handoff.
- Decide which reports are required weekly.
- Decide whether Growth Console stays internal or becomes partially productized.
