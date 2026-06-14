---
type: wiki
domain: zlicc
status: active
source_count: 6
last_reviewed: 2026-06-03
---

# Zlicc Event Platform Intelligence

This page collects event platform, CRM, Web AR, deployment, and channel architecture references from Codex exports.

## Event CRM And Platform

The event CRM material points toward a structured event operating system: attendees, registrations, leads, engagement, deployment, and data capture.

Primary snapshots:

- [[10 Raw Sources/Codex/2026-04-28/files-mentioned-by-the-user-hexagon/Zlicc Events CRM Product Blueprint|Zlicc Events CRM Product Blueprint]]
- [[10 Raw Sources/Codex/2026-04-28/files-mentioned-by-the-user-hexagon/DATABASE_SCHEMA|Database Schema]]
- [[10 Raw Sources/Codex/2026-04-28/files-mentioned-by-the-user-hexagon/README_DEPLOYMENT|Deployment Notes]]

## Infrastructure Reference

The AWS reference is useful for thinking about multi-service event platform deployment and operational architecture.

Source: [[10 Raw Sources/Codex/2026-05-01/so-we-run-multiple-services-at/AWS_Event_Platform_Architecture_Reference|AWS Event Platform Architecture Reference]]

## Web AR And WhatsApp

Web AR and WhatsApp source snapshots should be treated as capability references:

- [[10 Raw Sources/Codex/2026-04-28/need-a-web-ar-application-which/README|Web AR Application README]]
- [[10 Raw Sources/Codex/2026-04-28/i-want-you-to-create-a/whatsapp-business-api-scope|WhatsApp Business API Scope]]

## How This Connects To Zlicc

- ZliccSync can own registration, access, check-in, lead capture, dashboards, and CRM/API exports.
- ZliccPulse can own live audience participation.
- ZliccAI can own summaries, assistants, captions, translation, and intelligence layers.
- ZliccXR can own Web AR and immersive product or brand interactions.
- ZliccLive can own streaming, hybrid, broadcast, and archive workflows.

## Open Loops

- Decide whether event CRM, Growth Console, and ZliccSync should share data contracts.
- Decide what belongs in an internal reusable platform versus client-specific builds.
- Define approved deployment patterns for small, medium, and enterprise-grade event systems.
- Build a clean event-platform capability matrix.
