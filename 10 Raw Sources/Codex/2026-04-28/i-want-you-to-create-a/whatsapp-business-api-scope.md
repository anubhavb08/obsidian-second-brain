# Scope Document: Direct Meta WhatsApp Business Platform Integration

Version: 1.0  
Date: 2026-04-28  
Owner: Product and Engineering  
Context: Direct integration with Meta Business Manager, WhatsApp Business Account, and WhatsApp Cloud API. No third-party BSP, CRM messaging vendor, or campaign provider is assumed.

## 1. Executive Summary

This document defines the scope for building a first-party WhatsApp Business Platform capability that can be reused across Zlicc products, including campaign management, event registration infrastructure, CRM, future customer engagement products, internal operations, and product-triggered notifications.

The core objective is to create a reusable WhatsApp communication layer that supports all meaningful WhatsApp Business Platform interactions available through direct Meta integration:

- Business onboarding through Meta Business Manager and WhatsApp Business Account setup.
- Phone number registration, verification, profile, quality, billing, and messaging limits.
- Outbound campaigns using approved message templates.
- Inbound and outbound customer conversations within the service window.
- Agent, automation, CRM, and event lifecycle messaging.
- Rich message types: text, media, contacts, location, reactions, templates, interactive messages, product/catalog messages, flows, payments where supported, typing indicators, read receipts, and message status events.
- Webhook ingestion for messages, delivery/read statuses, errors, account changes, template changes, phone quality changes, and policy events.
- Consent, opt-out, compliance, data retention, auditability, and operational monitoring.

This scope assumes the app is not a general-purpose AI chatbot product. Business-specific automation for customer support, event registration, reminders, CRM follow-ups, order flows, and lead handling can be included, subject to Meta policy review.

## 2. Goals

### 2.1 Product Goals

- Let internal teams create, approve, schedule, send, and monitor WhatsApp campaigns.
- Let future products call a shared WhatsApp service instead of building separate integrations.
- Support transactional, lifecycle, marketing, support, event, and CRM workflows.
- Provide a unified conversation inbox and timeline per contact.
- Provide a template management layer for Meta-approved message templates.
- Provide reusable APIs for Zlicc products to send WhatsApp messages safely.
- Provide reliable webhook processing and message state tracking.
- Provide opt-in, opt-out, consent, and communication preference management.

### 2.2 Engineering Goals

- Integrate directly with Meta Graph API and WhatsApp Cloud API.
- Centralize WABA, phone number, token, template, media, and webhook management.
- Expose an internal messaging API for products such as events, CRM, marketing, sales, support, and future apps.
- Maintain idempotency, retries, deduplication, message audit logs, and observability.
- Design for multiple WABAs, multiple phone numbers, multiple products, and multiple business units.
- Avoid provider lock-in while using Meta-native features directly.

### 2.3 Business Goals

- Reduce dependency on third-party WhatsApp vendors.
- Own customer communication data and CRM interaction history.
- Improve event attendance, lead conversion, support response time, and lifecycle engagement.
- Create a foundation for future Zlicc communication products.

## 3. Non-Goals

- Building a third-party BSP or reseller platform unless separately scoped.
- Supporting the deprecated On-Premises API as a primary integration path.
- Bypassing Meta template review, rate limits, quality systems, commerce rules, or user consent requirements.
- Sending unsolicited messages without opt-in.
- Using WhatsApp as the primary distribution channel for a general-purpose AI assistant.
- Replacing email, SMS, push notifications, or in-app notifications entirely.

## 4. Source References

These references should be rechecked during implementation because Meta APIs, template rules, pricing, and policy terms change frequently.

- Meta WhatsApp Platform Webhooks: https://developers.facebook.com/docs/whatsapp/webhooks
- Meta WhatsApp Cloud API Postman collection: https://www.postman.com/meta/whatsapp-business-platform/documentation/wlk6lh4/whatsapp-cloud-api
- Meta WhatsApp Cloud API Messages Object: https://www.postman.com/meta/whatsapp-business-platform/folder/fxug05h/messages-object
- Meta WhatsApp Flows API collection notice: https://www.postman.com/meta/whatsapp-business-platform/documentation/y5swede/moved-whatsapp-flows-api
- Meta Embedded Signup Postman collection: https://www.postman.com/meta/whatsapp-business-platform/collection/du6gzjv/embedded-signup
- Meta Developers WhatsApp Business Calling API overview video: https://www.youtube.com/watch?v=SRDjj3KAMIE
- Meta Business Platform docs landing: https://developers.facebook.com/docs/whatsapp

## 5. Key Platform Concepts

### 5.1 Meta Business Portfolio

The verified Meta business entity that owns or manages assets, apps, WABAs, users, system users, permissions, payment methods, and compliance status.

Scope requirements:

- Store Meta business portfolio ID.
- Track verification status.
- Track app review and permission status.
- Track business ownership and admin roles.
- Track billing/payment configuration if exposed through available APIs or internal admin checks.

### 5.2 Meta App

The developer app used to access Graph API and WhatsApp APIs.

Scope requirements:

- App mode and app review status.
- Required permissions such as WhatsApp messaging and management permissions.
- Webhook callback URL and verify token.
- App secret and signature validation.
- Token lifecycle management.

### 5.3 WhatsApp Business Account

A WABA is the WhatsApp business container for phone numbers, templates, business profile, quality, capabilities, and webhook subscriptions.

Scope requirements:

- Support one or more WABAs.
- Store WABA ID, display name, business owner, status, timezone, currency, and capabilities.
- Track WABA review status, restrictions, violations, and quality changes.
- Subscribe each WABA to webhooks.

### 5.4 WhatsApp Business Phone Number

The sender identity used to send and receive WhatsApp messages.

Scope requirements:

- Store phone number ID, display phone number, verified name, quality rating, messaging limit tier, status, and assigned products.
- Register, verify, and manage phone numbers where supported.
- Support multiple phone numbers per WABA.
- Route inbound messages by phone number ID.
- Route outbound messages using product, campaign, tenant, or business unit rules.

### 5.5 Customer Contact

The end user who has opted in to receive WhatsApp messages or who initiates a conversation.

Scope requirements:

- Store WhatsApp ID, E.164 phone number, name, profile name from webhook, locale, timezone, consent status, opt-out status, source, tags, CRM linkage, and product linkage.
- Maintain communication history and consent evidence.
- Merge duplicate contacts across CRM, event registration, and campaign imports.

## 6. User Roles

- Super Admin: Manages Meta app, WABAs, phone numbers, billing, permissions, and global settings.
- WhatsApp Admin: Manages templates, phone numbers, webhooks, sender health, and compliance.
- Campaign Manager: Creates audiences, campaigns, template personalization, schedules, and reports.
- CRM User: Sends one-to-one WhatsApp messages, views conversation history, and manages follow-ups.
- Support Agent: Handles inbound conversations, assignments, notes, and escalations.
- Event Operator: Sends event confirmations, reminders, check-in links, post-event follow-ups, and attendance messages.
- Product System User: Uses internal APIs to send transactional messages.
- Compliance Reviewer: Reviews consent, opt-out, template category, policy, and audit logs.
- Developer: Manages integration credentials, webhook debugging, logs, retries, and API usage.

## 7. WhatsApp Interaction Scope

This section defines every major WhatsApp interaction type the platform should account for.

### 7.1 Outbound Template Messages

Template messages are required when the business initiates a conversation or sends outside the customer service window. Templates must be created, submitted, approved, categorized, localized, versioned, and monitored.

Supported template categories:

- Marketing: promotions, offers, announcements, win-back, re-engagement, newsletters, product launches, invitations, event promotions.
- Utility: order updates, registration confirmations, tickets, reminders, account updates, invoices, payment confirmations, operational alerts.
- Authentication: OTP, verification code, login confirmation, account recovery, secure action confirmation.

Template components to support:

- Header: text, image, video, document, or none depending on template type.
- Body: text with variables.
- Footer: optional text.
- Buttons: quick reply, URL, phone number, copy code, flow button, catalog/product action where supported.
- Variables: contact, CRM fields, event fields, product fields, order fields, date/time, currency, custom merge tags.
- Languages: one template can have multiple localized variants.
- Media examples: required by Meta for approval in many media templates.

Functional scope:

- Template creation UI.
- Template approval status tracking.
- Template versioning and archival.
- Variable schema definition.
- Preview rendering for each language.
- Category selection and guardrails.
- Template quality monitoring.
- Disabled/rejected template handling.
- Template reuse across campaign, CRM, event, and automation modules.
- Template governance: who can create, edit, submit, approve internally, archive, or send.

### 7.2 Outbound Free-Form Session Messages

Free-form messages can be sent only when allowed by the active customer service window or another Meta-supported session rule.

Supported outbound free-form types:

- Text.
- Text with URL preview.
- Image by uploaded media ID or public URL.
- Video by uploaded media ID or public URL.
- Audio by uploaded media ID or public URL.
- Document by uploaded media ID or public URL.
- Sticker where supported.
- Contact card.
- Location.
- Reaction to a customer message.
- Reply to a specific message using message context.
- Interactive list message.
- Interactive reply button message.
- Single product message.
- Multi-product message.
- Catalog message.
- Flow message, where supported and configured.
- Typing indicator, where supported.
- Mark message as read.

Functional scope:

- Agent compose box.
- Automation send action.
- Internal API send endpoint.
- Message context and threaded reply support.
- Media upload and reuse.
- Delivery status tracking.
- Error display and retry.
- Permission checks based on product, team, sender number, and contact status.

### 7.3 Inbound Customer Messages

Inbound messages arrive through webhooks. They must be normalized, deduplicated, stored, and routed.

Inbound message types to support:

- Text.
- Image.
- Video.
- Audio and voice note.
- Document.
- Sticker.
- Contact.
- Location.
- Reaction.
- Interactive reply from button.
- Interactive reply from list.
- Flow response.
- Order or commerce response.
- Product inquiry.
- Button response from template.
- Quick reply payload.
- Unsupported message fallback.
- Deleted/revoked message indicator if provided by webhook behavior.
- System or customer identity update events such as phone number change.

Functional scope:

- Inbound webhook receiver.
- Signature verification.
- Idempotency by message ID.
- Contact creation or matching.
- Conversation opening and routing.
- Attachment download and storage.
- Customer profile name capture.
- Contact timeline update.
- Assignment rules.
- SLA timers.
- Notification to agents or product systems.
- Webhook replay tooling for debugging.

### 7.4 Message Status Events

Outbound messages produce status webhooks. These events power reporting, automation, and troubleshooting.

Statuses to support:

- Accepted by internal API.
- Sent to Meta.
- Meta accepted.
- Sent.
- Delivered.
- Read.
- Failed.
- Deleted or unavailable where applicable.
- Pricing/category metadata.
- Error code and reason.

Functional scope:

- Store all status transitions with timestamps.
- Show per-recipient delivery state.
- Aggregate campaign metrics.
- Trigger fallback workflows on failure.
- Suppress repeat sends after permanent failure.
- Expose status to calling products through callbacks or polling.

### 7.5 Conversation Window and Session Management

Scope requirements:

- Track customer service window per contact and sender phone number.
- Distinguish business-initiated and user-initiated conversations.
- Enforce template requirement outside the service window.
- Display whether free-form reply is currently allowed.
- Trigger internal reminders before session expiry.
- Record conversation category and pricing metadata where provided.
- Prevent agent or automation sends that violate platform rules.

### 7.6 Reactions

Scope requirements:

- Allow agents or automations to react to inbound messages where supported.
- Receive and display customer reactions.
- Support reaction removal/update events where available.
- Store the referenced message ID.

### 7.7 Replies and Contextual Messaging

Scope requirements:

- Send a message as a reply to a specific inbound or outbound message where supported.
- Display quoted message preview.
- Preserve context across CRM, support, and event timelines.
- Allow automation to branch based on reply payload or context.

### 7.8 Media Messaging

Media scope:

- Upload media to Meta.
- Send media by media ID.
- Send media by link where supported.
- Receive media webhooks.
- Download media securely.
- Store media metadata: type, MIME type, size, checksum if available, filename, caption, expiry, storage location, source.
- Support image, video, audio, voice note, document, and sticker.
- Enforce file size, type, and security restrictions.
- Virus scan downloaded files before internal display or forwarding.

### 7.9 Contacts

Scope requirements:

- Send contact cards with name, phone, email, organization, address, and URL fields.
- Receive contact cards from customers.
- Allow saving received contact cards into CRM as new leads or linked contacts.
- Prevent accidental overwrite of existing CRM contacts without review.

### 7.10 Location

Scope requirements:

- Send static location with latitude, longitude, name, and address.
- Receive customer-shared location.
- Display map preview.
- Link location to event venue, support ticket, field visit, or lead record.
- Handle privacy and retention rules for location data.

### 7.11 Interactive Reply Buttons

Use cases:

- RSVP yes/no.
- Confirm registration.
- Accept terms.
- Choose a follow-up action.
- Request callback.
- Select language.
- Confirm attendance.
- Support triage.

Scope requirements:

- Compose up to the platform-supported button count.
- Store button IDs separately from display labels.
- Route replies by payload ID.
- Support analytics by button.
- Support localization.

### 7.12 Interactive List Messages

Use cases:

- Choose event slot.
- Choose product interest.
- Choose support issue.
- Choose CRM pipeline action.
- Choose location or branch.
- Choose appointment time.

Scope requirements:

- Create sections and rows.
- Store stable row IDs.
- Process selected row webhooks.
- Support dynamic list generation from products/events/CRM.
- Provide fallbacks when list size exceeds limits.

### 7.13 WhatsApp Flows

Flows enable structured, in-WhatsApp forms and multi-step experiences.

Use cases:

- Event registration.
- Lead capture.
- Appointment booking.
- Contact us.
- Customer support intake.
- Surveys.
- Sign-up/sign-in.
- Feedback forms.
- CRM qualification.
- Product onboarding.

Scope requirements:

- Create and manage flows.
- Associate flows with WABAs and phone numbers.
- Define endpoint URI for flow data exchange.
- Build flow schemas and versions.
- Validate submitted data.
- Map flow responses to CRM, event registration, support tickets, or product records.
- Handle unsupported WhatsApp client versions with fallback messages.
- Track flow open, submit, abandon, and error events where available.
- Secure flow endpoint, including encryption/decryption if required by current Meta Flow endpoint rules.

### 7.14 Commerce, Catalog, and Product Messages

Use cases:

- Send catalog link.
- Send single product.
- Send multi-product selection.
- Receive product inquiry.
- Receive order object where commerce is enabled.
- CRM sales follow-up.

Scope requirements:

- Connect or reference Meta catalog.
- Map catalog products to internal product IDs.
- Send catalog, single product, and multi-product messages.
- Receive orders and product inquiries.
- Convert commerce interactions into CRM leads, deals, or order workflows.
- Respect commerce eligibility and country restrictions.

### 7.15 Payments

Payments availability is country-specific and may depend on Meta feature eligibility. Meta's Postman collection exposes regional Payments API folders, including India and Singapore, but production eligibility must be confirmed before implementation.

Potential use cases:

- Paid event registration.
- Invoice payment.
- Deposit collection.
- Order checkout.
- Renewal payment.

Scope requirements:

- Treat payments as conditional feature flags by country, WABA, and product.
- Do not store raw payment credentials unless explicitly required and compliant.
- Reconcile payment status with event/CRM/order records.
- Provide non-WhatsApp fallback payment links.
- Coordinate with legal, finance, and compliance before launch.

### 7.16 QR Codes and Click-to-WhatsApp Entry Points

Use cases:

- Event booth scan.
- Website "chat on WhatsApp".
- Campaign landing page.
- Product support entry.
- CRM lead capture.
- Physical venue posters.

Scope requirements:

- Generate tracked wa.me links or QR codes where supported.
- Attach source, campaign, product, and UTM metadata.
- Start conversations from inbound customer message.
- Trigger welcome automation after customer initiation.
- Attribute leads and conversions.

### 7.17 Block, Opt-Out, and User Preference Events

Scope requirements:

- Let users opt out through keywords such as STOP, UNSUBSCRIBE, CANCEL, or localized equivalents.
- Let agents mark a contact as opted out.
- Support per-channel and per-topic preferences.
- Suppress campaign sends to opted-out contacts.
- Preserve transactional send eligibility only if allowed by policy and consent model.
- Record evidence: timestamp, source, keyword, campaign, phone number, agent/system actor.
- Respect customer blocks or delivery failures that imply non-reachability.

### 7.18 Account, Template, and Phone Health Events

Webhook and admin scope:

- Template approved, rejected, paused, disabled, or quality-changed.
- Phone number quality rating change.
- Messaging limit tier change.
- WABA review or capability change.
- Display name approval/rejection.
- Policy violation or restriction.
- App permission issue.
- Token expiration or revocation.

Functional scope:

- Admin alerts.
- Sender health dashboard.
- Send suppression when sender or template is restricted.
- Root cause notes and remediation workflow.

### 7.19 WhatsApp Business Calling

WhatsApp Business Calling should be treated as a conditional, eligibility-gated capability. Meta has introduced bi-directional calling use cases for the WhatsApp Business Platform, including user-initiated calling and business-initiated calling, but availability, region support, pricing, SDK/API access, and approval requirements must be confirmed with current Meta documentation before implementation.

Use cases:

- Escalate high-intent leads from chat to voice.
- Allow event attendees to call support from the WhatsApp thread.
- Allow support agents to request or initiate a call when chat is insufficient.
- Handle missed-call callback requests.
- Preserve chat and call context in one CRM/contact timeline.
- Route calls to sales, support, onboarding, or event operations.

Scope requirements:

- Feature flag by WABA, phone number, region, and product.
- Admin setting to enable or disable calling on eligible numbers.
- User-initiated call handling.
- Business-initiated call request/permission flow where required.
- Call state tracking: requested, ringing, answered, missed, declined, completed, failed.
- Agent availability and routing.
- CRM and event timeline logging.
- Call notes and dispositions.
- Compliance review for recording, if recording is ever supported or added through telephony infrastructure.
- Fallback to text or regular phone call when WhatsApp calling is unavailable.

## 8. Product Modules

### 8.1 Meta Integration Admin

Features:

- Connect Meta business assets.
- Store WABA and phone number metadata.
- Manage access tokens and token health.
- Configure webhook callback URL.
- Subscribe WABAs to webhooks.
- Manage sender phone numbers.
- View profile, display name, quality, and messaging limits.
- Configure business profile.
- Configure product-to-sender routing.
- View audit log of integration changes.

### 8.2 Template Manager

Features:

- Create templates.
- Select category.
- Define components.
- Add variables.
- Upload sample media.
- Add translations.
- Submit for Meta approval.
- Track approval lifecycle.
- Preview on mobile-like renderer.
- Lock approved templates from unsafe edits.
- Archive unused templates.
- Monitor quality and rejection reasons.

### 8.3 Campaign Builder

Features:

- Campaign objective: marketing, event, CRM, lifecycle, announcement, reactivation, feedback, support follow-up.
- Audience source: CSV, CRM segment, event segment, product segment, custom query, manual list.
- Consent validation.
- Deduplication.
- Template selection.
- Variable mapping.
- Test send.
- Schedule send.
- Throttle/rate control.
- Timezone-aware delivery.
- Exclusion lists.
- Frequency caps.
- Approval workflow.
- Campaign pause/resume/cancel.
- A/B template testing.
- Link tracking.
- Conversion tracking.

Metrics:

- Sent.
- Delivered.
- Read.
- Failed.
- Reply rate.
- Button/list click rate.
- Flow open/submission rate.
- Opt-out rate.
- Conversion rate.
- Cost estimate/actual where pricing data is available.

### 8.4 Conversation Inbox

Features:

- Unified contact timeline.
- Conversation list by status, team, agent, SLA, source, product, and phone number.
- Assign/unassign agent.
- Internal notes.
- Tags.
- Saved replies.
- Template send from inbox.
- Free-form send when session is open.
- Media attachments.
- Reply context.
- Message status indicators.
- Customer profile panel.
- CRM/event/product context panel.
- Escalation and handoff.
- Close/reopen conversation.

### 8.5 CRM Integration

Use cases:

- Create lead from inbound WhatsApp.
- Send template from lead/contact/deal.
- Log all WhatsApp interactions in CRM timeline.
- Trigger follow-up tasks from replies.
- Update deal stage from button/list responses.
- Route hot leads to sales agents.
- Trigger reactivation campaigns.
- Manage consent and preferences.

Required CRM objects:

- Contact.
- Lead.
- Account/company.
- Deal/opportunity.
- Activity.
- Task.
- Campaign.
- Consent record.
- Conversation.

### 8.6 Event Registration Integration

Use cases:

- Event invite.
- Registration confirmation.
- Ticket or QR code delivery.
- Reminder sequences.
- Location and parking information.
- Agenda updates.
- Speaker/session updates.
- Check-in instructions.
- Waitlist update.
- Cancellation/update alerts.
- Post-event feedback flow.
- Certificate or resource delivery.
- No-show follow-up.

Integration requirements:

- Trigger messages on registration lifecycle events.
- Support Flow-based registration inside WhatsApp.
- Map attendee status to WhatsApp campaign segments.
- Log all interactions to attendee profile.
- Respect opt-in source and event-specific consent.

### 8.7 Internal Messaging API

Expose a product-safe API layer so every Zlicc product does not call Meta directly.

Core endpoints:

- Create or update contact.
- Check contact consent and send eligibility.
- Send template message.
- Send session message.
- Upload media.
- Get message status.
- Get conversation timeline.
- Register webhook callback for product-level events.
- Create campaign request.
- Create event notification request.
- Upsert template variable schema.

API requirements:

- Idempotency keys.
- Product/app authentication.
- Per-product quotas.
- Sender routing policy.
- Error normalization.
- Audit logging.
- Async status callbacks.

## 9. Automation Scope

Automation should be business-specific and bound to product workflows.

Supported triggers:

- Inbound message received.
- Keyword detected.
- Button/list reply received.
- Flow submitted.
- Template delivered/read.
- Message failed.
- User opted out.
- Event registration created/updated.
- CRM stage changed.
- Task due.
- Campaign reply received.
- Support ticket created/closed.

Supported actions:

- Send template.
- Send session message.
- Assign agent.
- Add tag.
- Update CRM field.
- Create task.
- Create ticket.
- Add to campaign segment.
- Remove from campaign segment.
- Trigger webhook to product.
- Start WhatsApp Flow.
- Pause automation.

Guardrails:

- Enforce consent.
- Enforce session window.
- Enforce template category.
- Enforce frequency caps.
- Prevent infinite loops.
- Prevent prohibited general-purpose AI use.
- Keep human handoff available for support flows.

## 10. Consent and Compliance Scope

### 10.1 Opt-In

Acceptable opt-in sources may include:

- Website form.
- Event registration form.
- CRM import with documented consent.
- In-app setting.
- WhatsApp user-initiated message.
- QR code entry.
- Checkout or payment form.
- Manual admin entry with evidence.

Data to store:

- Phone number.
- Consent status.
- Consent source.
- Consent text shown to user.
- Timestamp.
- IP/user agent where applicable.
- Product or event context.
- Topics consented to.
- Proof artifact or form submission ID.

### 10.2 Opt-Out

Requirements:

- Global opt-out.
- Topic-level opt-out.
- Campaign-level unsubscribe.
- Manual opt-out by agent.
- Keyword-based opt-out.
- Suppression before send.
- Exportable audit history.

### 10.3 Template and Campaign Governance

Requirements:

- Internal campaign approval for marketing broadcasts.
- Template category review.
- Prohibited content checks.
- Audience consent checks.
- Frequency cap checks.
- Test send before launch.
- Emergency stop.
- Campaign audit trail.

### 10.4 Privacy and Data Retention

Requirements:

- Define retention periods for messages, media, webhook payloads, logs, and consent records.
- Encrypt sensitive data at rest.
- Restrict access by role.
- Redact or purge media on retention expiry.
- Provide export/delete workflows if required by applicable law.
- Avoid storing sensitive payment, health, or government ID information unless separately approved and secured.

## 11. Data Model

Core entities:

- MetaBusinessPortfolio.
- MetaApp.
- WhatsAppBusinessAccount.
- WhatsAppPhoneNumber.
- WhatsAppBusinessProfile.
- WhatsAppTemplate.
- WhatsAppTemplateVersion.
- WhatsAppTemplateLanguage.
- WhatsAppTemplateComponent.
- WhatsAppMediaAsset.
- Contact.
- ContactConsent.
- ContactPreference.
- Conversation.
- Message.
- MessageStatusEvent.
- WebhookEvent.
- Campaign.
- CampaignAudience.
- CampaignRecipient.
- CampaignSendJob.
- CampaignMetric.
- FlowDefinition.
- FlowSubmission.
- CommerceProductMapping.
- PaymentAttempt.
- AutomationRule.
- AgentAssignment.
- AuditLog.

Message fields:

- Internal message ID.
- Meta message ID.
- Direction: inbound/outbound.
- Sender phone number ID.
- Customer WhatsApp ID.
- Contact ID.
- Conversation ID.
- Type.
- Template ID/version/language if applicable.
- Content payload.
- Media IDs.
- Context/reply-to message ID.
- Status.
- Error code/message.
- Pricing/category metadata where available.
- Product source.
- Campaign ID.
- Event ID.
- CRM object IDs.
- Created/sent/delivered/read/failed timestamps.

## 12. Webhook Processing

Webhook receiver requirements:

- Public HTTPS endpoint with valid TLS certificate.
- Verify token challenge endpoint.
- Validate Meta request signature.
- Parse object, entry, change, field, and value structure.
- Persist raw payload for audit/debugging with retention rules.
- Deduplicate by webhook event and message/status IDs.
- Process asynchronously through queue.
- Retry failed processing.
- Route by WABA ID and phone number ID.
- Normalize payload into internal event model.
- Emit internal events to CRM, campaign, inbox, event infrastructure, and automations.

Webhook categories to handle:

- Inbound messages.
- Outbound message statuses.
- Customer profile or phone number updates.
- Message errors.
- Template status updates.
- WABA review/capability changes.
- Phone number display name status changes.
- Phone number quality changes.
- Policy violations or account restrictions.

## 13. API Integration Scope

Meta API areas:

- WABA management.
- Phone number registration and management.
- Business profile.
- Webhook subscriptions.
- Media upload/download.
- Messages send endpoint.
- Template creation and management.
- Flows management.
- Catalog and commerce messaging.
- QR codes.
- Analytics.
- Billing/pricing where exposed.
- Block users where supported.
- Business compliance endpoints where supported.

Internal integration principles:

- Products call internal WhatsApp service, not Meta directly.
- Meta errors are normalized into stable internal error codes.
- Internal service owns retries and idempotency.
- All sends are checked against consent, sender health, template status, and policy guardrails.

## 14. Campaign Scope by Use Case

### 14.1 Marketing Campaigns

Examples:

- Product launch.
- Offer announcement.
- Re-engagement.
- Newsletter.
- Event promotion.
- Webinar invite.

Requirements:

- Opt-in required.
- Approved marketing template required.
- Audience suppression and frequency caps.
- Campaign approval workflow.
- Opt-out handling.

### 14.2 Utility Campaigns

Examples:

- Registration confirmation.
- Event reminder.
- Order update.
- Account update.
- Payment reminder.
- Document delivery.

Requirements:

- Utility template.
- Triggered by user transaction or existing relationship.
- Personalization accuracy.
- Failure fallback path.

### 14.3 Authentication Campaigns

Examples:

- OTP.
- Login verification.
- Account recovery.
- Secure action confirmation.

Requirements:

- Authentication template.
- Short expiry.
- Anti-abuse limits.
- No marketing content.
- Security audit logs.

### 14.4 Support and Service Conversations

Examples:

- Inbound customer support.
- Agent reply.
- Automated triage.
- Ticket follow-up.
- Feedback request.

Requirements:

- Free-form session messaging only when allowed.
- Template re-entry when session closed.
- Assignment and SLA.
- Human handoff.

## 15. Reporting and Analytics

Dashboards:

- Sender health.
- Template health.
- Campaign performance.
- Conversation volume.
- Agent performance.
- Event messaging performance.
- CRM conversion impact.
- Failure/error analysis.
- Opt-out trends.
- Cost and pricing trend where data is available.

Metrics:

- Total sends.
- Sent, delivered, read, failed.
- Delivery latency.
- Read latency.
- Reply rate.
- Button/list selection rate.
- Flow start/submit/drop-off.
- Conversion rate.
- Revenue/event attendance attributed.
- Opt-out rate.
- Template rejection/disable count.
- Phone quality changes.
- Error code distribution.

## 16. Reliability and Operations

Requirements:

- Queue-based sending.
- Per-phone-number rate limiting.
- Backoff and retry for transient Meta errors.
- Dead letter queue for failed jobs.
- Idempotency for product API calls and webhook events.
- Circuit breaker for restricted phone/template/WABA.
- Monitoring and alerting.
- Replay failed webhook events.
- Manual resend for failed campaign recipients where safe.
- Export logs for debugging.

Operational alerts:

- Webhook endpoint failing.
- Token expired/revoked.
- Template rejected/disabled.
- Phone quality dropped.
- Messaging limit changed.
- High send failure rate.
- Campaign opt-out spike.
- Media download failures.
- Queue backlog.
- Meta API rate limit.

## 17. Security Scope

Requirements:

- Encrypt tokens and secrets.
- Rotate tokens.
- Validate webhook signatures.
- Least-privilege access to admin functions.
- Role-based access control.
- Audit all template, campaign, consent, and sender changes.
- Mask phone numbers where appropriate.
- Secure media download URLs.
- Virus scan inbound media.
- Prevent SSRF through media URL handling.
- Restrict export permissions.
- Protect internal send APIs with product credentials and scopes.

## 18. Policy and Risk Considerations

Risks:

- Meta policy changes can affect templates, pricing, AI automation, commerce, payments, or eligibility.
- Poor campaign quality can reduce phone quality and messaging limits.
- Missing consent can cause user complaints and account restrictions.
- Template miscategorization can lead to rejection or enforcement.
- Direct integration means Zlicc owns uptime, retries, compliance, observability, and support.

Mitigations:

- Maintain a policy review checklist.
- Add campaign approval workflow.
- Add sender health monitoring.
- Keep a compliance kill switch.
- Revalidate Meta docs before major releases.
- Use feature flags for region-sensitive features such as payments.

## 19. Phased Delivery Plan

### Phase 1: Foundation

- Meta app and WABA connection.
- Phone number metadata sync.
- Webhook receiver.
- Send template message.
- Receive inbound text and status events.
- Basic contact and conversation storage.
- Consent and opt-out foundation.
- Admin sender health view.

### Phase 2: Campaigns

- Template manager.
- Audience import/segments.
- Campaign builder.
- Scheduling and throttling.
- Delivery/read/failure reporting.
- Opt-out suppression.
- Test send and approval workflow.

### Phase 3: Inbox and CRM

- Conversation inbox.
- Agent assignment.
- Free-form session messages.
- Media send/receive.
- CRM timeline integration.
- Lead creation from inbound WhatsApp.
- Follow-up tasks and tags.

### Phase 4: Event Infrastructure

- Event registration triggers.
- Confirmation, reminder, ticket, and feedback templates.
- Flow-based registration.
- Attendance and conversion reporting.
- Event-specific consent handling.

### Phase 5: Advanced Interactions

- Interactive lists and buttons.
- WhatsApp Flows.
- Catalog/product messages.
- QR code entry points.
- Typing indicators and richer agent UX.
- Automation rules.

### Phase 6: Commerce and Payments

- Product catalog mapping.
- Order/product inquiry handling.
- Payment workflows where eligible.
- Finance reconciliation.
- Regional compliance review.

## 20. Acceptance Criteria

The platform is considered scope-complete when:

- Admins can connect and monitor Meta/WABA/phone assets directly.
- Approved templates can be created, sent, localized, and tracked.
- Campaign managers can run compliant campaigns with reporting.
- Inbound messages and status webhooks are reliably processed.
- CRM and event systems can send through internal APIs.
- All major WhatsApp message types are represented in the internal model.
- Consent and opt-out are enforced before outbound sends.
- Sender/template/account health issues suppress unsafe sends.
- Agents can manage live conversations within allowed session rules.
- Webhook, send, campaign, template, and consent activity is auditable.

## 21. Open Questions

- Will the first release support one WABA only, or multiple WABAs from day one?
- Will this platform support only Zlicc-owned WABAs, or customer-owned WABAs through embedded signup later?
- Which products launch first: campaigns, events, CRM, or support inbox?
- What is the canonical contact database: CRM, identity service, or WhatsApp service?
- What consent model should be enforced for transactional versus marketing messages?
- Which countries must be supported at launch?
- Will payments be included for India in the first commerce release?
- What retention period should apply to WhatsApp message bodies and media?
- Which automation features require human approval before sending?
- What policy review process should be used for AI-assisted support replies?

## 22. Implementation Checklist

- Create Meta app and verify required permissions.
- Configure WABA and sender phone number.
- Configure webhook callback and verify token.
- Subscribe WABA to webhook fields.
- Build webhook receiver with signature validation.
- Build normalized message/event schema.
- Build outbound send service.
- Build template sync and management.
- Build media upload/download service.
- Build consent and opt-out service.
- Build campaign send queue.
- Build status aggregation.
- Build CRM/event integration APIs.
- Build admin dashboards.
- Build observability and alerting.
- Run policy, security, and privacy review.
