# Zlicc Growth Console Engineering Backlog

Version: 0.1  
Created: 2026-05-21  
Source PRD: `Zlicc_Growth_Console_V1_PRD.md`  
Purpose: Translate the V1 PRD into engineering epics, user stories, database schema, and sprint sequencing.

---

## 1. Build Assumptions

This backlog assumes the actual V1 build, not a lightweight prototype.

Recommended product shape:

- Frontend: Next.js or equivalent React framework.
- Backend: Node.js/NestJS or equivalent structured API framework.
- Database: PostgreSQL.
- Queue/cache: Redis.
- Workers: background jobs for AI runs, enrichment, webhooks, scoring, reports, and scheduled checks.
- Storage: AWS S3.
- Deployment: AWS EC2 with Docker Compose, Nginx, SSL, backups, and monitoring.
- AI: OpenAI API for CMO Brain and specialist agents.
- Integrations: Apollo, SendGrid, Microsoft Graph, WhatsApp Business API provider, Make where useful.

Engineering posture:

- Build modularly, but avoid overengineering V1.
- Store enough audit trails to explain AI decisions, approvals, sends, and score changes.
- Keep LinkedIn human-in-loop.
- Keep personal WhatsApp manual.
- Keep Bigin as lifecycle CRM outside the V1 core.

---

## 2. Backlog Priority System

| Priority | Meaning |
| --- | --- |
| P0 | Required for V1 launch or foundational dependency |
| P1 | Required for strong V1 usefulness, but can ship after initial foundation |
| P2 | Valuable enhancement that should not block launch |
| V2 | Explicitly deferred |

Story states:

- Backlog.
- Ready.
- In progress.
- In review.
- Done.
- Deferred.

---

## 3. Epic Map

| Epic ID | Epic | Priority | Primary Owner |
| --- | --- | --- | --- |
| E01 | Product Foundation, Auth, RBAC | P0 | Platform |
| E02 | Growth Data Core | P0 | Backend |
| E03 | Manual Capture, Imports, Files | P0 | Full stack |
| E04 | CMO Brain And Agent Operations | P0 | AI/backend |
| E05 | Apollo Prospecting And Enrichment | P0 | Integrations |
| E06 | LinkedIn Workbench | P0 | Full stack |
| E07 | Seasonal Calendar And Campaign Portfolio | P0 | Full stack |
| E08 | Landing Page Builder And Publisher | P0 | Full stack |
| E09 | Content Studio, Publishing Calendar, Newsletters | P0 | Full stack |
| E10 | Content Quality And Compliance Engine | P0 | AI/backend |
| E11 | Creative Production Desk And Asset Library | P1 | Full stack |
| E12 | Email Campaigns And SendGrid Events | P0 | Integrations |
| E13 | Outlook Reply Intelligence | P0 | Integrations/AI |
| E14 | WhatsApp AI Sales Assistant | P0 | Integrations/AI |
| E15 | Warm Signals, Lead Scoring, Tasks | P0 | Backend |
| E16 | Analytics And Weekly CMO Report | P1 | Full stack |
| E17 | Deployment, Security, Observability | P0 | Platform |
| E18 | Bigin Handoff And Make Automation Bridge | P2 | Integrations |

---

## 4. Epics And User Stories

### E01: Product Foundation, Auth, RBAC

Goal: Establish the application shell, authentication, roles, permissions, navigation, and admin foundations.

#### E01-US01: App Shell And Navigation

Priority: P0  
As a user, I want a consistent Growth Console shell so that I can move between Today, Leads, Campaigns, Content, Outreach, Assets, and Analytics.

Acceptance criteria:

- Sidebar or primary navigation includes all V1 modules.
- User role controls visible modules.
- Empty states are implemented for all top-level screens.
- Layout works on desktop and tablet-width screens.

#### E01-US02: User Authentication

Priority: P0  
As an admin, I want secure login so that only authorized Zlicc users can access the console.

Acceptance criteria:

- Login/logout works.
- Password reset or admin invite path exists.
- Session expiry is handled.
- API routes reject unauthenticated requests.

#### E01-US03: Role-Based Access Control

Priority: P0  
As an admin, I want roles and permissions so that operators and creative users only access their relevant workflows.

Acceptance criteria:

- Roles exist for Admin, Founder/Marketing Owner, LinkedIn Operator, Creative Team Member, Sales/Handoff Owner.
- Restricted screens and actions are blocked in both UI and API.
- Permission checks are covered by tests.
- Attempts to access unauthorized routes are logged.

#### E01-US04: Admin User Management

Priority: P1  
As an admin, I want to invite and manage users so that the team can work inside the console.

Acceptance criteria:

- Admin can invite user by email.
- Admin can assign role.
- Admin can deactivate user.
- Deactivated users cannot log in.

#### E01-US05: System Settings

Priority: P1  
As an admin, I want central settings so that integrations, defaults, scoring weights, and approval rules are manageable.

Acceptance criteria:

- Settings screen exists.
- Integration keys are not shown in plaintext after save.
- Approval thresholds and lead scoring weights can be stored.
- Settings changes are audit logged.

---

### E02: Growth Data Core

Goal: Build the underlying data model and UI/API foundation for accounts, contacts, leads, tasks, notes, and interactions.

#### E02-US01: Account Management

Priority: P0  
As a user, I want to create and view company accounts so that prospects can be grouped by organization.

Acceptance criteria:

- Create, edit, view, and list accounts.
- Account supports industry, website, LinkedIn URL, city, segment, status, and source.
- Account detail shows linked contacts, leads, campaigns, notes, and interactions.
- Duplicate warning appears for matching company name or website.

#### E02-US02: Contact Management

Priority: P0  
As a user, I want to manage contacts so that individual prospects can be tracked.

Acceptance criteria:

- Create, edit, view, and list contacts.
- Contact supports name, role, seniority, email, phone, WhatsApp status, LinkedIn URL, and source.
- Contact can belong to an account.
- Duplicate warning appears for matching email, phone, or LinkedIn URL.

#### E02-US03: Lead Pipeline

Priority: P0  
As a user, I want a lead pipeline so that growth prospects can move through stages.

Acceptance criteria:

- Lead stages include spotted, qualified, warmed, connected, enriched, outreach ready, contacted, replied, meeting booked, proposal requested, nurture, lost, won, suppressed.
- Lead has score, score reason, source, recommended offer, recommended pillars, owner, and next-best action.
- Stage changes are written to timeline.
- Lead list supports filters by stage, score, source, campaign, owner, and next action due.

#### E02-US04: Tasks And Follow-Ups

Priority: P0  
As a user, I want tasks so that follow-ups are never lost.

Acceptance criteria:

- Tasks have type, owner, due date, priority, status, linked lead/contact/account/campaign, and notes.
- Today screen shows due and overdue tasks.
- Tasks can be completed, snoozed, reassigned, or cancelled.
- Task changes are logged.

#### E02-US05: Notes And Timeline

Priority: P0  
As a user, I want a timeline so that all lead activity is visible in one place.

Acceptance criteria:

- Notes can be added to accounts, contacts, leads, and campaigns.
- Timeline shows notes, tasks, stage changes, outreach, replies, warm signals, agent outputs, and approvals.
- Timeline items are timestamped and attributed to user, system, integration, or agent.
- Timeline can be filtered by event type.

#### E02-US06: Consent And Suppression Foundation

Priority: P0  
As an admin, I want consent and suppression records so that outreach respects opt-outs and channel rules.

Acceptance criteria:

- Contact has email consent, WhatsApp consent, unsubscribe, do-not-contact, and suppression status.
- Outreach APIs check suppression before sending or queuing messages.
- Opt-out events update contact and lead state.
- Suppression status is visible on lead and contact detail.

---

### E03: Manual Capture, Imports, Files

Goal: Allow quick entry of personal WhatsApp briefs, calls, referrals, existing contacts, and uploaded evidence without automating personal inboxes.

#### E03-US01: Quick Capture Form

Priority: P0  
As the founder, I want a simple form to capture brief details from personal WhatsApp or calls so that informal opportunities become structured leads.

Acceptance criteria:

- Form supports name, company, mobile, email, LinkedIn URL, source, brief notes, solution/event type, files/links, and follow-up date.
- System matches existing contacts/accounts before creating new ones.
- New records are created when no match exists.
- CMO Brain scoring task is queued after save.

#### E03-US02: File Uploads To S3

Priority: P0  
As a user, I want to upload files so that briefs, decks, images, and proof assets are preserved.

Acceptance criteria:

- Upload supports PDF, PPT/PPTX, DOC/DOCX, images, videos, and common archives.
- Files are stored in S3 with metadata in database.
- Files can be linked to leads, campaigns, production tasks, and proof assets.
- Upload size and file type limits are enforced.

#### E03-US03: Existing Customer CSV Import

Priority: P1  
As a user, I want to import existing contacts and companies so that warm audiences can be educated and expanded.

Acceptance criteria:

- CSV import supports mapping columns to account/contact fields.
- Import preview shows create/update/skipped counts.
- Duplicate detection runs before import.
- Imported contacts can be tagged as existing customer, past client, agency, or partner.

#### E03-US04: Import Error Handling

Priority: P1  
As a user, I want import errors explained so that bad rows can be corrected.

Acceptance criteria:

- Failed rows show reason.
- User can download an error CSV.
- Partial import success is supported.
- Import job status is visible.

---

### E04: CMO Brain And Agent Operations

Goal: Implement the AI orchestration layer, specialist agent registry, run logs, approvals, and recommendation outputs.

#### E04-US01: CMO Brain Configuration

Priority: P0  
As an admin, I want the CMO Brain configured from Zlicc's strategy documents so that recommendations follow Zlicc's positioning.

Acceptance criteria:

- CMO Brain prompt/config can reference `Zlicc_CMO_Brain.md` content.
- Config version is stored for every AI run.
- Admin can view current config version.
- Changes require admin permission.

#### E04-US02: Lead Classification And Scoring

Priority: P0  
As a marketing owner, I want CMO Brain to classify and score leads so that we know who deserves attention.

Acceptance criteria:

- Lead scoring can be triggered manually or automatically after capture/import/enrichment.
- Output includes score, score reasons, segment, recommended offer, pillar stack, and next-best action.
- Score update creates a timeline entry.
- Low confidence outputs are flagged for review.

#### E04-US03: Agent Registry

Priority: P0  
As an admin, I want a registry of specialist agents so that each agent's purpose and permissions are clear.

Acceptance criteria:

- Registry includes Market Research, Prospecting, Content Strategy, Creative Briefing, WhatsApp Sales Assistant, Reply Intelligence, Analytics, Compliance.
- Each agent stores purpose, allowed inputs, allowed tools, output type, approval requirement, escalation rules, and status.
- Agents can be enabled/disabled.
- Agent config changes are audit logged.

#### E04-US04: Agent Run Logs

Priority: P0  
As a founder, I want to inspect AI agent runs so that I can trust and audit their work.

Acceptance criteria:

- Each run stores agent, trigger, input references, output, status, token/cost estimate, quality score, and errors.
- Agent outputs can be linked to leads, campaigns, tasks, content, or assets.
- Failed runs show actionable error state.
- Runs can be retried by authorized users.

#### E04-US05: Approval Queue For AI Outputs

Priority: P0  
As a founder, I want AI outputs routed for approval so that campaigns are not activated blindly.

Acceptance criteria:

- Approval queue supports approve, reject, edit, request revision, and comment.
- Public content, landing pages, newsletters, campaigns, pricing, claims, and client references require approval.
- Approval state is stored on the output object.
- Approval actions are timeline/audit logged.

#### E04-US06: Cost Metering For AI Runs

Priority: P1  
As an admin, I want to track AI usage so that OpenAI spend remains controlled.

Acceptance criteria:

- Agent runs store approximate tokens and estimated cost where available.
- Monthly usage summary is visible.
- Admin can set soft alert threshold.
- Non-critical scheduled agent runs can be paused.

---

### E05: Apollo Prospecting And Enrichment

Goal: Use Apollo as the structured prospect search and enrichment source.

#### E05-US01: Apollo Integration Setup

Priority: P0  
As an admin, I want Apollo API settings so that prospecting and enrichment can run from the console.

Acceptance criteria:

- Apollo credentials are stored securely.
- API connectivity can be tested.
- Failed connection shows readable error.
- Credentials are not exposed after save.

#### E05-US02: Prospect Search Import

Priority: P0  
As a prospecting user, I want to import Apollo prospects into a campaign so that targeted lists can be built quickly.

Acceptance criteria:

- User can define search metadata such as industry, role, seniority, location, company size, and campaign.
- Imported records are deduplicated against contacts/accounts.
- Leads are created with source Apollo and linked campaign where selected.
- Import job records created, updated, skipped, and failed counts.

#### E05-US03: Lead Enrichment

Priority: P0  
As a user, I want to enrich selected leads so that email, phone, role, and company data are available.

Acceptance criteria:

- Enrichment can be triggered from lead detail and list views.
- Returned fields update contact/account only when confidence/source rules pass.
- Original and updated values are tracked.
- Enrichment status is visible.

#### E05-US04: Enrichment Queue

Priority: P1  
As a system, I want enrichment jobs queued so that API limits and failures are handled gracefully.

Acceptance criteria:

- Jobs process in background worker.
- Rate limit and retry logic exists.
- Failed jobs can be retried.
- Job status appears in admin/integration logs.

---

### E06: LinkedIn Workbench

Goal: Support manual LinkedIn prospecting, operator task execution, suggested copy, and result logging without scraping or automation.

#### E06-US01: Add LinkedIn Prospect

Priority: P0  
As a user, I want to add a LinkedIn prospect URL and note so that LinkedIn discovery enters the growth pipeline.

Acceptance criteria:

- Form captures LinkedIn URL, name, company, role, relationship source, notes, campaign tag, and priority.
- URL is validated for basic LinkedIn format.
- Existing contact/lead matching runs before save.
- CMO Brain scoring and next action is queued after save.

#### E06-US02: LinkedIn Operator Queue

Priority: P0  
As a LinkedIn Operator, I want a daily queue so that I know which profiles need manual action.

Acceptance criteria:

- Queue shows today, overdue, high priority, replied, and snoozed tabs.
- Each task card shows context, score, reason, offer, suggested action, and profile link.
- Operator can only see assigned tasks unless admin.
- Opening a LinkedIn link is a normal manual link-out.

#### E06-US03: Suggested LinkedIn Copy

Priority: P0  
As an operator, I want suggested comments and messages so that I can act quickly while staying on-brand.

Acceptance criteria:

- Suggested copy types include comment, connection note, first DM, and follow-up DM.
- Copy is generated from lead/campaign context.
- Operator can copy text but the system does not auto-send.
- Copy output has approval or confidence indicator where needed.

#### E06-US04: Manual Outcome Logging

Priority: P0  
As an operator, I want to log LinkedIn outcomes so that the CRM knows what happened.

Acceptance criteria:

- Outcomes include done, skipped, no relevant post, connection sent, connected, DM sent, replied, not relevant, snoozed.
- Outcome updates lead timeline and warm signals where applicable.
- Positive outcomes can create follow-up tasks.
- Replied outcome asks for a short response summary.

#### E06-US05: LinkedIn Permissions

Priority: P0  
As an admin, I want LinkedIn Operator restrictions enforced so that strategy and lead scoring stay protected.

Acceptance criteria:

- Operator cannot edit lead score, CMO recommendation, campaign strategy, API keys, or delete leads.
- API rejects restricted actions.
- Permission tests cover critical restrictions.
- UI hides restricted controls.

---

### E07: Seasonal Calendar And Campaign Portfolio

Goal: Plan multiple targeted campaigns in parallel using market timing, manual Zlicc knowledge, and a maximum three active lane rule.

#### E07-US01: Seasonal Opportunity Calendar

Priority: P0  
As a marketing owner, I want an editable seasonal calendar so that campaign planning reflects both market timing and Zlicc experience.

Acceptance criteria:

- User can create, edit, archive, and view opportunities.
- Fields include name, category, planning window, event window, audience, industries, offer, pillars, priority, source, notes, repeat yearly, reminders.
- Manual entries are clearly marked.
- Calendar supports list and month/quarter views.

#### E07-US02: AI Seasonal Suggestions

Priority: P1  
As a marketing owner, I want AI to suggest seasonal opportunities so that we do not miss timing windows.

Acceptance criteria:

- Market Research Agent can create suggested opportunities in pending state.
- User can approve, edit, reject, or merge suggestions.
- Suggestions are not hard-coded to AGM, GFF, or example events.
- Source/reason is stored for every suggestion.

#### E07-US03: Opportunity Reminders

Priority: P0  
As a user, I want reminders before planning windows so that campaigns start early.

Acceptance criteria:

- Reminder offsets support 90, 60, 45, and 30 days.
- Reminders create tasks or notifications.
- Reminders can be disabled per opportunity.
- Completed reminders are logged.

#### E07-US04: Campaign Lane Builder

Priority: P0  
As a marketing owner, I want to create campaign lanes so that each audience has a focused plan.

Acceptance criteria:

- Campaign lane includes name, trigger, audience, roles, prospect list, offer, pillars, landing page, content set, LinkedIn plan, outreach sequence, creative tasks, owner, priority, status, metrics.
- Campaign can be linked to seasonal opportunity.
- Campaign can be draft, scheduled, active, paused, completed, archived.
- CMO Brain can draft campaign lane recommendations.

#### E07-US05: Three Active Campaign Limit

Priority: P0  
As a system, I want to enforce a maximum of three active campaign lanes so that execution stays focused.

Acceptance criteria:

- System blocks activation of a fourth active campaign.
- Active campaign dashboard shows current capacity.
- Tiering supports up to two aggressive prospecting lanes and one nurture/education/agency lane.
- Admin override requires reason and audit log.

---

### E08: Landing Page Builder And Publisher

Goal: Generate, edit, approve, and publish campaign landing pages inside Growth Console without manual HTML upload.

#### E08-US01: Landing Page Template Library

Priority: P0  
As a marketing owner, I want fixed premium templates so that campaign pages can be created quickly.

Acceptance criteria:

- Templates include Agency Tech Partner, ZliccPulse Activity Menu, AI Event Experience Kit, Exhibition Booth Intelligence, Hybrid AGM/Webcast, Product Launch Experience, Existing Customer Expansion.
- Each template has editable sections.
- Template preview exists.
- Template metadata includes recommended offer and pillar fit.

#### E08-US02: Landing Page Draft Generation

Priority: P0  
As a marketing owner, I want page drafts generated from campaign context so that landing pages are not written from scratch.

Acceptance criteria:

- CMO Brain generates headline, subheadline, problem, offer, pillar stack, use cases, proof suggestions, CTA, and form copy.
- Draft is editable.
- Draft is linked to campaign.
- Draft is routed through approval before publish.

#### E08-US03: Landing Page Editor

Priority: P0  
As a user, I want to edit landing page content so that AI output can be improved before publishing.

Acceptance criteria:

- User can edit all text fields.
- User can attach approved assets/proof.
- User can configure WhatsApp CTA and form fields.
- Changes are versioned.

#### E08-US04: Landing Page Publish

Priority: P0  
As a marketing owner, I want one-click publish so that approved pages go live under Zlicc-controlled URLs.

Acceptance criteria:

- Publish generates slug and hosted page.
- SSL works in production.
- Page status changes to published.
- Published page can be unpublished.
- No manual HTML upload required.

#### E08-US05: Landing Page Forms And Tracking

Priority: P0  
As a system, I want form and CTA events tracked so that landing pages create leads and warm signals.

Acceptance criteria:

- Form submission creates or updates lead/contact/account.
- UTM parameters are captured.
- CTA clicks and downloads create warm signals where trackable.
- Submissions are visible on campaign and lead timelines.

---

### E09: Content Studio, Publishing Calendar, Newsletters

Goal: Create campaign-aware content drafts, plan LinkedIn formats, manage newsletters, and route outputs for approval.

#### E09-US01: Content Asset Model And List

Priority: P0  
As a user, I want a content library so that all drafts and approved content are organized.

Acceptance criteria:

- Content assets store campaign, channel, asset type, title, body/script, CTA, status, owner, approval status, quality score.
- List supports filters by campaign, channel, type, status, owner.
- Content detail shows versions, comments, approval, and related tasks.
- Approved assets can be reused.

#### E09-US02: Campaign Content Generator

Priority: P0  
As a marketing owner, I want campaign content generated from strategy so that every piece is targeted.

Acceptance criteria:

- Generates LinkedIn post, carousel outline, video script, WhatsApp copy, email copy, article outline, and deck/one-pager outline where selected.
- Uses audience, offer, pillars, campaign trigger, and CTA.
- Output is linked to campaign.
- Output enters approval or quality review workflow.

#### E09-US03: LinkedIn Publishing Calendar

Priority: P0  
As a marketing owner, I want a LinkedIn calendar so that posts are distributed across the week.

Acceptance criteria:

- Calendar supports company page and founder/profile drafts.
- Formats include text POV, document/carousel, poll, short video, proof/image post, article, newsletter, case-study post, landing-page post.
- Calendar prevents all active campaign posts from being planned on one day unless approved.
- Posts can be marked draft, ready, approved, published manually, or skipped.

#### E09-US04: Newsletter Engine

Priority: P1  
As a marketing owner, I want monthly newsletters so that warm audiences and LinkedIn followers are educated consistently.

Acceptance criteria:

- Newsletter type supports LinkedIn and email.
- Edition stores topic, month, audience, campaigns referenced, sections, CTA, approval status.
- CMO Brain can draft newsletter outline and body.
- Newsletter requires approval before publishing/sending.

#### E09-US05: Content Comments And Revision Flow

Priority: P1  
As a reviewer, I want comments and revision history so that content can improve before approval.

Acceptance criteria:

- Reviewer can comment on content asset.
- User can create revised version.
- Version history is visible.
- Final approved version is clearly marked.

---

### E10: Content Quality And Compliance Engine

Goal: Score drafts and block risky content before public use.

#### E10-US01: Quality Scorecard

Priority: P0  
As a marketing owner, I want every draft scored so that weak content is improved before approval.

Acceptance criteria:

- Scorecard covers strategy, audience specificity, pillar accuracy, offer clarity, proof, CTA, tone, channel fit, visual brief quality, compliance.
- Score and reason are stored on content asset.
- Low-scoring drafts are marked needs revision.
- Reviewer can override with reason.

#### E10-US02: Compliance Guardrail Checks

Priority: P0  
As a founder, I want unsafe claims blocked so that Zlicc does not publish risky statements.

Acceptance criteria:

- Checks flag pricing promises, delivery guarantees, unapproved client references, unapproved capability claims, missing unsubscribe, and opt-out concerns.
- High-risk outputs require human approval.
- Blocked reasons are shown.
- Compliance Agent run is logged.

#### E10-US03: Revision Loop

Priority: P1  
As a content owner, I want AI-assisted revision so that failed drafts can be improved quickly.

Acceptance criteria:

- User can request revision based on scorecard feedback.
- Revised draft creates new version.
- Previous version remains accessible.
- Revision run is linked to original quality result.

---

### E11: Creative Production Desk And Asset Library

Goal: Convert campaign needs into designer/editor tasks and manage final files, proof, approvals, and reuse.

#### E11-US01: Production Task Buckets

Priority: P1  
As a creative team member, I want assigned task buckets so that I know what to produce.

Acceptance criteria:

- Buckets support designer, video editor, copywriter, strategist, content operator.
- Tasks show brief, campaign, asset type, specs, deadline, priority, and status.
- Creative users see only assigned or relevant tasks.
- Task changes are logged.

#### E11-US02: Creative Brief Generator

Priority: P1  
As a marketing owner, I want creative briefs generated from campaign context so that designers receive clear direction.

Acceptance criteria:

- Brief includes audience, offer, pillar, copy/script, references, format, size, duration, CTA, and quality checklist.
- Brief is editable.
- Brief can be assigned to user.
- Brief links back to campaign and content asset.

#### E11-US03: Creative Uploads And Versions

Priority: P1  
As a creative team member, I want to upload source and final files so that campaign assets are managed centrally.

Acceptance criteria:

- Upload supports source files, exports, thumbnails, and notes.
- Each upload creates version metadata.
- Reviewer can compare latest version notes.
- Approved version is clearly marked.

#### E11-US04: Asset Library

Priority: P1  
As a user, I want approved assets stored in a library so that content and landing pages can reuse them.

Acceptance criteria:

- Assets store type, title, tags, campaign, pillar, use case, file, status, permission, owner.
- Library supports search and filters.
- Only approved assets appear in public-use selectors by default.
- Internal-only assets are visually marked.

#### E11-US05: Proof Vault Lite

Priority: P1  
As a marketing owner, I want to upload proof from activations so that campaigns can use evidence.

Acceptance criteria:

- Proof assets support client, industry, pillar, use case, permission status, public/internal visibility, and metrics.
- CMO Brain can recommend proof assets.
- Public content cannot use unapproved proof without warning/approval.
- Proof can be linked to campaign and landing page.

---

### E12: Email Campaigns And SendGrid Events

Goal: Send approved email campaigns through an email platform and sync delivery/engagement events.

#### E12-US01: SendGrid Integration Setup

Priority: P0  
As an admin, I want SendGrid settings so that campaign emails can be sent from a proper email platform.

Acceptance criteria:

- API key stored securely.
- Sender/domain status can be configured or documented.
- Webhook endpoint for events is available.
- Test event can be processed.

#### E12-US02: Email Sequence Builder

Priority: P0  
As a marketing owner, I want approved email sequences so that outreach can be structured.

Acceptance criteria:

- Sequence stores campaign, audience, subject, body, follow-up steps, delay, sender, reply-to, and approval status.
- Sequence cannot send unless approved.
- Suppressed/unsubscribed contacts are excluded.
- Test send is available to internal users.

#### E12-US03: Campaign Email Sending

Priority: P0  
As a system, I want to send approved emails so that campaigns can reach selected prospects.

Acceptance criteria:

- User can select approved segment/list.
- System checks suppression before queueing.
- Sends are logged per recipient.
- Failed sends show reason.

#### E12-US04: SendGrid Event Sync

Priority: P0  
As a system, I want email events synced so that warm signals and statuses update.

Acceptance criteria:

- Webhook handles delivered, bounced, opened, clicked, unsubscribed, spam report, dropped.
- Events link to contact, lead, campaign, and outreach message where possible.
- Bounces/unsubscribes update suppression/consent.
- Opens/clicks create warm signals based on scoring rules.

---

### E13: Outlook Reply Intelligence

Goal: Use Microsoft 365 Outlook/Graph to classify inbound replies to campaign emails and update lead status.

#### E13-US01: Microsoft Graph OAuth Setup

Priority: P0  
As an admin, I want Microsoft Graph connected so that the system can read relevant replies from the Outlook mailbox.

Acceptance criteria:

- OAuth connection flow works for authorized mailbox.
- Tokens are stored securely.
- Admin can disconnect/reconnect.
- Permission failure states are readable.

#### E13-US02: Reply Detection

Priority: P0  
As a system, I want to detect campaign replies so that interested leads are not missed.

Acceptance criteria:

- System polls or subscribes to mailbox events.
- Replies are matched to campaign/contact using sender, thread metadata, reply-to, or tracking metadata.
- Non-campaign mail is ignored where possible.
- Duplicates are prevented.

#### E13-US03: Reply Classification

Priority: P0  
As a marketing owner, I want replies classified so that hot leads are prioritized.

Acceptance criteria:

- Categories include interested, meeting requested, send details, proposal requested, not now, not relevant, wrong person, referral, unsubscribe/remove, negative sentiment, out of office.
- Classification stores confidence and reason.
- High-intent replies create urgent task.
- Unsubscribe/remove updates suppression.

#### E13-US04: Reply Timeline And Task Creation

Priority: P0  
As a sales owner, I want reply summaries and tasks so that I can follow up quickly.

Acceptance criteria:

- Reply summary appears on lead timeline.
- Task is created for interested, meeting, proposal, send details, referral, and negative sentiment cases.
- Owner can mark task handled.
- Lead score/stage updates based on classification.

---

### E14: WhatsApp AI Sales Assistant

Goal: Handle approved WABA campaign replies, qualify leads, and hand off to humans when needed.

#### E14-US01: WABA Provider Integration

Priority: P0  
As an admin, I want WhatsApp Business API connected so that campaign replies can enter the console.

Acceptance criteria:

- Provider credentials/webhook configured securely.
- Inbound messages create or update conversation sessions.
- Outbound template send can be tested internally.
- Webhook signature or equivalent validation is implemented where supported.

#### E14-US02: WhatsApp Template Library

Priority: P0  
As a marketing owner, I want approved template records so that WhatsApp outreach stays controlled.

Acceptance criteria:

- Templates store name, category, language, body, CTA, approval status, provider template ID, and use case.
- Only approved templates can be sent in campaign flow.
- Template sends are logged.
- Opt-out language can be included.

#### E14-US03: WhatsApp AI Assistant Responses

Priority: P0  
As a system, I want the assistant to answer first-level replies using approved knowledge so that prospects get quick responses.

Acceptance criteria:

- Assistant uses approved offer summaries, landing page links, deck links, and FAQs.
- Assistant can ask qualifying questions.
- Every bot response is logged.
- Low-confidence responses trigger handoff instead of guessing.

#### E14-US04: WhatsApp Human Handoff

Priority: P0  
As a sales owner, I want bot handoffs so that important conversations reach a human quickly.

Acceptance criteria:

- Handoff triggers include pricing, proposal, meeting request, complex brief, negative sentiment, low confidence, repeated back-and-forth, high lead score, strategic account.
- Handoff creates urgent task.
- Bot stops autonomous response after handoff where configured.
- Lead timeline shows handoff reason.

#### E14-US05: WhatsApp Opt-Out Handling

Priority: P0  
As a system, I want opt-outs handled immediately so that WhatsApp compliance is respected.

Acceptance criteria:

- Remove/stop/not interested intent is detected.
- Contact WhatsApp consent/suppression is updated.
- Confirmation response can be sent if approved.
- Future WhatsApp sends are blocked.

---

### E15: Warm Signals, Lead Scoring, Tasks

Goal: Convert interactions into scoring, urgency, and next actions.

#### E15-US01: Warm Signal Model

Priority: P0  
As a system, I want a unified warm signal model so that all engagement can influence lead priority.

Acceptance criteria:

- Signal stores type, source, lead, contact, account, campaign, score delta, reason, metadata, timestamp.
- Supported sources include email, Outlook, WhatsApp, landing page, downloads, LinkedIn logs, meetings.
- Signals appear on lead timeline.
- Signals can be filtered by type and campaign.

#### E15-US02: Lead Score Recalculation

Priority: P0  
As a marketing owner, I want score updates from signals so that active prospects rise to the top.

Acceptance criteria:

- Scoring rules combine profile fit, campaign fit, engagement, reply intent, channel eligibility, and suppression status.
- Score recalculates after meaningful signals.
- Score changes store previous score, new score, reason.
- Suppressed leads cannot stay in active outreach stages.

#### E15-US03: Next-Best Action Engine

Priority: P0  
As a user, I want the system to recommend next actions so that follow-up is clear.

Acceptance criteria:

- Actions include LinkedIn task, email follow-up, WhatsApp handoff, send details, book meeting, nurture, suppress, enrich, review manually.
- Recommendation is visible on lead list and detail.
- Recommendation includes reason.
- User can accept, override, or dismiss.

#### E15-US04: Task Automation Rules

Priority: P1  
As a system, I want tasks created from high-value signals so that follow-ups are not missed.

Acceptance criteria:

- Meeting request creates urgent sales task.
- Proposal request creates urgent founder/sales task.
- Landing page form creates follow-up task.
- Repeated click/download can create warm follow-up task.
- Task creation rules are configurable.

---

### E16: Analytics And Weekly CMO Report

Goal: Provide operational and campaign intelligence for decision-making.

#### E16-US01: Campaign Dashboard

Priority: P1  
As a founder, I want a campaign dashboard so that I know which lanes are working.

Acceptance criteria:

- Dashboard shows active lanes, leads, sends, replies, meetings, landing page conversions, warm signals, and current recommendation.
- Metrics can be filtered by date, campaign, channel, audience, offer.
- Paused/completed campaigns remain viewable.
- Dashboard data updates from events and signals.

#### E16-US02: Lead Source And Channel Dashboard

Priority: P1  
As a marketing owner, I want source/channel analytics so that I know where quality leads come from.

Acceptance criteria:

- Sources include Apollo, LinkedIn manual, quick capture, existing customer import, landing page, referral, event.
- Channels include email, WhatsApp, LinkedIn, landing page, manual.
- Dashboard shows conversion by stage.
- Data can be exported.

#### E16-US03: Creative Production Dashboard

Priority: P1  
As a founder, I want production visibility so that campaign delays are visible.

Acceptance criteria:

- Shows tasks by owner, status, due date, campaign, and asset type.
- Highlights overdue and blocked tasks.
- Shows average revision count and approval cycle.
- Links to task details.

#### E16-US04: Weekly CMO Report

Priority: P1  
As a founder, I want a weekly report so that campaign decisions are easy.

Acceptance criteria:

- Report covers active lanes, performance, warm leads, replies, meetings, content status, landing page performance, creative bottlenecks, and recommended next actions.
- Report can be generated on demand.
- Report can be saved to weekly archive.
- CMO Brain recommendations include rationale.

---

### E17: Deployment, Security, Observability

Goal: Ship V1 on AWS EC2 with secure operations, backups, logs, and environment separation.

#### E17-US01: Docker Compose Production Stack

Priority: P0  
As an engineer, I want Docker Compose services so that the app can run reliably on one EC2 instance.

Acceptance criteria:

- Services include web, api, worker, postgres, redis, nginx.
- Health checks exist for main services.
- Environment variables are externalized.
- Restart policies are configured.

#### E17-US02: EC2 Deployment

Priority: P0  
As an admin, I want the app deployed to AWS EC2 so that the team can use it.

Acceptance criteria:

- EC2 instance provisioned with required ports and security groups.
- Domain/subdomain points to Nginx.
- SSL certificate installed.
- Deployment runbook exists.

#### E17-US03: Backups

Priority: P0  
As an admin, I want database and asset backup strategy so that data can be recovered.

Acceptance criteria:

- PostgreSQL daily backup to S3.
- Backup retention policy defined.
- Restore process documented and tested at least once on staging/dev.
- S3 bucket permissions are restricted.

#### E17-US04: Logs And Error Monitoring

Priority: P0  
As an engineer, I want logs and error visibility so that production issues can be diagnosed.

Acceptance criteria:

- API, worker, webhook, and integration errors are logged.
- Critical failures surface in admin/system logs.
- Sensitive data is not logged.
- Log retention policy is defined.

#### E17-US05: Audit Logging

Priority: P0  
As an admin, I want audit logs so that sensitive actions are traceable.

Acceptance criteria:

- Audit logs include approvals, sends, suppression changes, API key changes, role changes, agent config changes, publish actions.
- Audit log records actor, action, entity, timestamp, before/after where safe.
- Admin can view and filter audit logs.
- Audit logs cannot be edited from UI.

---

### E18: Bigin Handoff And Make Automation Bridge

Goal: Support low-friction external workflow bridges without turning V1 into a full CRM migration.

#### E18-US01: Qualified Lead Export

Priority: P2  
As a sales owner, I want to export qualified leads so that they can be entered into Bigin when needed.

Acceptance criteria:

- Export includes account, contact, lead score, campaign, source, notes, interactions summary, next action.
- Export can be CSV.
- Export is permission-controlled.
- Export event is logged.

#### E18-US02: Make Webhook Bridge

Priority: P2  
As an admin, I want optional Make webhooks so that temporary automations can be connected quickly.

Acceptance criteria:

- Admin can configure outbound webhook endpoints for selected events.
- Webhook events can include lead created, task created, hot reply, creative approved, landing page form submitted.
- Failed webhook delivery is logged.
- Sensitive payload fields can be excluded.

---

## 5. First-Pass Database Schema

This schema is intended as an implementation starting point. It favors PostgreSQL with UUID primary keys, JSONB metadata for integration payloads, and explicit auditability for AI, approvals, and outreach.

### 5.1 Shared Enums

```sql
-- Suggested enum domains. Engineering may implement as PostgreSQL enums
-- or constrained text columns depending on migration preference.

role_key:
  admin, founder_marketing_owner, linkedin_operator, creative_team_member,
  sales_handoff_owner

lead_stage:
  spotted, qualified, warmed, connected, enriched, outreach_ready,
  contacted, replied, meeting_booked, proposal_requested, nurture,
  lost, won, suppressed

campaign_status:
  draft, scheduled, active, paused, completed, archived

task_status:
  open, in_progress, done, snoozed, cancelled

approval_status:
  not_required, pending, approved, rejected, needs_revision

channel:
  linkedin, email, whatsapp, landing_page, manual, phone, event, referral

content_status:
  draft, in_review, needs_revision, approved, published, archived

asset_permission_status:
  internal_only, public_approved, client_permission_required, rejected
```

### 5.2 Identity And Access

```sql
users (
  id uuid primary key,
  email text unique not null,
  name text not null,
  phone text,
  status text not null default 'active',
  created_at timestamptz not null default now(),
  updated_at timestamptz not null default now()
)

roles (
  id uuid primary key,
  key text unique not null,
  name text not null,
  description text
)

user_roles (
  user_id uuid references users(id),
  role_id uuid references roles(id),
  primary key (user_id, role_id)
)

permissions (
  id uuid primary key,
  key text unique not null,
  description text
)

role_permissions (
  role_id uuid references roles(id),
  permission_id uuid references permissions(id),
  primary key (role_id, permission_id)
)
```

### 5.3 Growth Core

```sql
accounts (
  id uuid primary key,
  company_name text not null,
  website text,
  linkedin_url text,
  industry text,
  city text,
  country text,
  segment text,
  account_type text,
  status text not null default 'active',
  source text,
  owner_id uuid references users(id),
  metadata jsonb not null default '{}',
  created_at timestamptz not null default now(),
  updated_at timestamptz not null default now()
)

contacts (
  id uuid primary key,
  account_id uuid references accounts(id),
  name text not null,
  title text,
  seniority text,
  department text,
  email text,
  phone text,
  whatsapp_number text,
  whatsapp_status text,
  linkedin_url text,
  source text,
  owner_id uuid references users(id),
  metadata jsonb not null default '{}',
  created_at timestamptz not null default now(),
  updated_at timestamptz not null default now()
)

leads (
  id uuid primary key,
  account_id uuid references accounts(id),
  contact_id uuid references contacts(id),
  campaign_id uuid,
  source text not null,
  stage text not null default 'spotted',
  score int not null default 0,
  score_reason text,
  segment text,
  recommended_offer_id uuid,
  recommended_pillars text[],
  next_best_action text,
  owner_id uuid references users(id),
  priority text default 'medium',
  status text not null default 'active',
  last_activity_at timestamptz,
  metadata jsonb not null default '{}',
  created_at timestamptz not null default now(),
  updated_at timestamptz not null default now()
)

notes (
  id uuid primary key,
  entity_type text not null,
  entity_id uuid not null,
  body text not null,
  created_by uuid references users(id),
  created_at timestamptz not null default now()
)

tasks (
  id uuid primary key,
  title text not null,
  description text,
  task_type text not null,
  status text not null default 'open',
  priority text not null default 'medium',
  owner_id uuid references users(id),
  lead_id uuid references leads(id),
  contact_id uuid references contacts(id),
  account_id uuid references accounts(id),
  campaign_id uuid,
  due_at timestamptz,
  completed_at timestamptz,
  snoozed_until timestamptz,
  metadata jsonb not null default '{}',
  created_at timestamptz not null default now(),
  updated_at timestamptz not null default now()
)

timeline_events (
  id uuid primary key,
  entity_type text not null,
  entity_id uuid not null,
  event_type text not null,
  title text not null,
  body text,
  actor_type text not null, -- user, system, integration, agent
  actor_id uuid,
  metadata jsonb not null default '{}',
  created_at timestamptz not null default now()
)
```

Recommended indexes:

```sql
create index idx_accounts_company_name on accounts using gin (to_tsvector('english', company_name));
create index idx_contacts_email on contacts(email);
create index idx_contacts_phone on contacts(phone);
create index idx_contacts_linkedin_url on contacts(linkedin_url);
create index idx_leads_stage_score on leads(stage, score desc);
create index idx_leads_campaign on leads(campaign_id);
create index idx_tasks_owner_status_due on tasks(owner_id, status, due_at);
create index idx_timeline_entity on timeline_events(entity_type, entity_id, created_at desc);
```

### 5.4 Consent And Suppression

```sql
consent_records (
  id uuid primary key,
  contact_id uuid references contacts(id) not null,
  channel text not null,
  status text not null, -- opted_in, implied, unknown, opted_out, suppressed
  source text,
  reason text,
  captured_at timestamptz not null default now(),
  expires_at timestamptz,
  metadata jsonb not null default '{}'
)

suppression_records (
  id uuid primary key,
  contact_id uuid references contacts(id),
  email text,
  phone text,
  channel text not null,
  reason text not null,
  source text,
  created_at timestamptz not null default now()
)
```

### 5.5 Capture And Imports

```sql
manual_captures (
  id uuid primary key,
  lead_id uuid references leads(id),
  contact_id uuid references contacts(id),
  account_id uuid references accounts(id),
  source text not null,
  brief_notes text not null,
  solution_or_event_type text,
  next_follow_up_at timestamptz,
  captured_by uuid references users(id),
  metadata jsonb not null default '{}',
  created_at timestamptz not null default now()
)

linkedin_prospect_captures (
  id uuid primary key,
  lead_id uuid references leads(id),
  contact_id uuid references contacts(id),
  account_id uuid references accounts(id),
  linkedin_url text not null,
  relationship_source text,
  notes text,
  priority text default 'medium',
  campaign_id uuid,
  captured_by uuid references users(id),
  created_at timestamptz not null default now()
)

import_jobs (
  id uuid primary key,
  import_type text not null,
  status text not null,
  source_file_asset_id uuid,
  created_count int default 0,
  updated_count int default 0,
  skipped_count int default 0,
  failed_count int default 0,
  error_file_asset_id uuid,
  created_by uuid references users(id),
  metadata jsonb not null default '{}',
  created_at timestamptz not null default now(),
  completed_at timestamptz
)
```

### 5.6 Campaigns And Seasonal Calendar

```sql
offers (
  id uuid primary key,
  name text not null,
  description text,
  primary_audience text,
  recommended_pillars text[],
  status text not null default 'active',
  metadata jsonb not null default '{}',
  created_at timestamptz not null default now(),
  updated_at timestamptz not null default now()
)

pillars (
  id uuid primary key,
  key text unique not null,
  name text not null,
  description text,
  status text not null default 'active'
)

seasonal_opportunities (
  id uuid primary key,
  name text not null,
  category text,
  planning_start date,
  planning_end date,
  event_start date,
  event_end date,
  audience text,
  industries text[],
  recommended_offer_id uuid references offers(id),
  relevant_pillars text[],
  priority text default 'medium',
  source text not null, -- manual, ai_suggested, imported
  notes text,
  repeat_yearly boolean default false,
  status text not null default 'active',
  created_by uuid references users(id),
  metadata jsonb not null default '{}',
  created_at timestamptz not null default now(),
  updated_at timestamptz not null default now()
)

opportunity_reminders (
  id uuid primary key,
  seasonal_opportunity_id uuid references seasonal_opportunities(id),
  reminder_offset_days int not null,
  reminder_at timestamptz not null,
  task_id uuid references tasks(id),
  status text not null default 'pending',
  created_at timestamptz not null default now()
)

campaigns (
  id uuid primary key,
  name text not null,
  seasonal_opportunity_id uuid references seasonal_opportunities(id),
  audience text,
  target_roles text[],
  offer_id uuid references offers(id),
  pillar_stack text[],
  priority_tier text,
  status text not null default 'draft',
  owner_id uuid references users(id),
  start_date date,
  end_date date,
  landing_page_id uuid,
  metrics jsonb not null default '{}',
  metadata jsonb not null default '{}',
  created_at timestamptz not null default now(),
  updated_at timestamptz not null default now()
)

campaign_leads (
  campaign_id uuid references campaigns(id),
  lead_id uuid references leads(id),
  status text not null default 'active',
  added_at timestamptz not null default now(),
  primary key (campaign_id, lead_id)
)
```

### 5.7 Landing Pages

```sql
landing_page_templates (
  id uuid primary key,
  key text unique not null,
  name text not null,
  description text,
  recommended_offer_id uuid references offers(id),
  recommended_pillars text[],
  schema jsonb not null,
  status text not null default 'active',
  created_at timestamptz not null default now()
)

landing_pages (
  id uuid primary key,
  campaign_id uuid references campaigns(id),
  template_id uuid references landing_page_templates(id),
  title text not null,
  slug text unique,
  status text not null default 'draft',
  content jsonb not null default '{}',
  form_schema jsonb not null default '{}',
  whatsapp_cta text,
  published_url text,
  published_at timestamptz,
  approved_by uuid references users(id),
  approved_at timestamptz,
  created_by uuid references users(id),
  created_at timestamptz not null default now(),
  updated_at timestamptz not null default now()
)

landing_page_events (
  id uuid primary key,
  landing_page_id uuid references landing_pages(id),
  campaign_id uuid references campaigns(id),
  lead_id uuid references leads(id),
  contact_id uuid references contacts(id),
  event_type text not null, -- visit, form_submit, download, whatsapp_click
  utm_source text,
  utm_medium text,
  utm_campaign text,
  utm_content text,
  metadata jsonb not null default '{}',
  occurred_at timestamptz not null default now()
)
```

### 5.8 Content, Assets, Production, Proof

```sql
content_assets (
  id uuid primary key,
  campaign_id uuid references campaigns(id),
  title text not null,
  asset_type text not null,
  channel text,
  body text,
  structured_content jsonb not null default '{}',
  cta text,
  status text not null default 'draft',
  approval_status text not null default 'pending',
  quality_score int,
  owner_id uuid references users(id),
  created_by uuid references users(id),
  metadata jsonb not null default '{}',
  created_at timestamptz not null default now(),
  updated_at timestamptz not null default now()
)

content_versions (
  id uuid primary key,
  content_asset_id uuid references content_assets(id),
  version_number int not null,
  body text,
  structured_content jsonb not null default '{}',
  created_by uuid references users(id),
  created_at timestamptz not null default now()
)

linkedin_post_plans (
  id uuid primary key,
  campaign_id uuid references campaigns(id),
  content_asset_id uuid references content_assets(id),
  profile_type text not null, -- company_page, founder_profile
  post_format text not null,
  scheduled_for timestamptz,
  status text not null default 'draft',
  approval_status text not null default 'pending',
  metadata jsonb not null default '{}',
  created_at timestamptz not null default now()
)

newsletter_editions (
  id uuid primary key,
  campaign_id uuid references campaigns(id),
  newsletter_type text not null, -- linkedin, email
  topic text not null,
  publish_month date not null,
  audience text,
  content_asset_id uuid references content_assets(id),
  status text not null default 'draft',
  approval_status text not null default 'pending',
  created_at timestamptz not null default now(),
  updated_at timestamptz not null default now()
)

file_assets (
  id uuid primary key,
  file_name text not null,
  mime_type text,
  size_bytes bigint,
  storage_provider text not null default 's3',
  storage_key text not null,
  public_url text,
  uploaded_by uuid references users(id),
  metadata jsonb not null default '{}',
  created_at timestamptz not null default now()
)

production_tasks (
  id uuid primary key,
  campaign_id uuid references campaigns(id),
  lead_id uuid references leads(id),
  content_asset_id uuid references content_assets(id),
  title text not null,
  assigned_to uuid references users(id),
  asset_type text not null,
  brief text,
  specs jsonb not null default '{}',
  status text not null default 'briefed',
  priority text not null default 'medium',
  due_at timestamptz,
  quality_score int,
  reviewer_comments text,
  created_by uuid references users(id),
  created_at timestamptz not null default now(),
  updated_at timestamptz not null default now()
)

production_task_files (
  id uuid primary key,
  production_task_id uuid references production_tasks(id),
  file_asset_id uuid references file_assets(id),
  version_number int not null,
  file_role text not null, -- source, export, thumbnail, reference
  notes text,
  uploaded_by uuid references users(id),
  created_at timestamptz not null default now()
)

proof_assets (
  id uuid primary key,
  title text not null,
  file_asset_id uuid references file_assets(id),
  client_name text,
  industry text,
  pillars text[],
  use_cases text[],
  permission_status text not null default 'internal_only',
  visibility text not null default 'internal',
  metrics jsonb not null default '{}',
  notes text,
  created_by uuid references users(id),
  created_at timestamptz not null default now(),
  updated_at timestamptz not null default now()
)
```

### 5.9 Outreach, Replies, Warm Signals

```sql
outreach_messages (
  id uuid primary key,
  lead_id uuid references leads(id),
  contact_id uuid references contacts(id),
  campaign_id uuid references campaigns(id),
  channel text not null,
  provider text,
  provider_message_id text,
  template_id uuid,
  subject text,
  body text,
  status text not null default 'draft',
  approval_status text not null default 'pending',
  sent_at timestamptz,
  metadata jsonb not null default '{}',
  created_at timestamptz not null default now(),
  updated_at timestamptz not null default now()
)

email_sequences (
  id uuid primary key,
  campaign_id uuid references campaigns(id),
  name text not null,
  sender_email text,
  reply_to_email text,
  status text not null default 'draft',
  approval_status text not null default 'pending',
  created_by uuid references users(id),
  created_at timestamptz not null default now(),
  updated_at timestamptz not null default now()
)

email_sequence_steps (
  id uuid primary key,
  sequence_id uuid references email_sequences(id),
  step_number int not null,
  delay_days int not null default 0,
  subject text not null,
  body text not null,
  created_at timestamptz not null default now()
)

email_events (
  id uuid primary key,
  outreach_message_id uuid references outreach_messages(id),
  provider_event_id text,
  event_type text not null,
  email text,
  metadata jsonb not null default '{}',
  occurred_at timestamptz not null default now()
)

outlook_replies (
  id uuid primary key,
  lead_id uuid references leads(id),
  contact_id uuid references contacts(id),
  campaign_id uuid references campaigns(id),
  outlook_message_id text unique,
  thread_id text,
  from_email text,
  subject text,
  body_excerpt text,
  classification text,
  confidence_score int,
  summary text,
  metadata jsonb not null default '{}',
  received_at timestamptz not null,
  created_at timestamptz not null default now()
)

whatsapp_templates (
  id uuid primary key,
  provider_template_id text,
  name text not null,
  category text,
  language text default 'en',
  body text not null,
  status text not null default 'draft',
  approval_status text not null default 'pending',
  metadata jsonb not null default '{}',
  created_at timestamptz not null default now(),
  updated_at timestamptz not null default now()
)

whatsapp_sessions (
  id uuid primary key,
  lead_id uuid references leads(id),
  contact_id uuid references contacts(id),
  phone text not null,
  status text not null default 'active',
  current_intent text,
  confidence_score int,
  handoff_status text,
  handoff_reason text,
  last_message_at timestamptz,
  metadata jsonb not null default '{}',
  created_at timestamptz not null default now(),
  updated_at timestamptz not null default now()
)

whatsapp_messages (
  id uuid primary key,
  session_id uuid references whatsapp_sessions(id),
  provider_message_id text,
  direction text not null, -- inbound, outbound
  sender_type text not null, -- prospect, bot, user, system
  body text,
  status text,
  metadata jsonb not null default '{}',
  occurred_at timestamptz not null default now()
)

warm_signals (
  id uuid primary key,
  lead_id uuid references leads(id),
  contact_id uuid references contacts(id),
  account_id uuid references accounts(id),
  campaign_id uuid references campaigns(id),
  signal_type text not null,
  source text not null,
  score_delta int not null default 0,
  reason text,
  metadata jsonb not null default '{}',
  occurred_at timestamptz not null default now()
)
```

Recommended indexes:

```sql
create index idx_outreach_lead_channel on outreach_messages(lead_id, channel, created_at desc);
create index idx_email_events_message on email_events(outreach_message_id, occurred_at desc);
create index idx_outlook_replies_from on outlook_replies(from_email, received_at desc);
create index idx_whatsapp_sessions_phone on whatsapp_sessions(phone);
create index idx_warm_signals_lead on warm_signals(lead_id, occurred_at desc);
create index idx_warm_signals_campaign on warm_signals(campaign_id, occurred_at desc);
```

### 5.10 AI, Approvals, Integrations, Audit

```sql
agent_definitions (
  id uuid primary key,
  key text unique not null,
  name text not null,
  purpose text,
  allowed_inputs jsonb not null default '[]',
  allowed_tools jsonb not null default '[]',
  output_type text,
  approval_required boolean not null default true,
  escalation_rules jsonb not null default '{}',
  status text not null default 'active',
  config jsonb not null default '{}',
  created_at timestamptz not null default now(),
  updated_at timestamptz not null default now()
)

agent_runs (
  id uuid primary key,
  agent_definition_id uuid references agent_definitions(id),
  triggered_by_type text not null, -- user, system, schedule, webhook
  triggered_by_id uuid,
  input_ref_type text,
  input_ref_id uuid,
  input_payload jsonb not null default '{}',
  output_payload jsonb not null default '{}',
  status text not null default 'queued',
  quality_score int,
  confidence_score int,
  prompt_version text,
  model text,
  token_input int,
  token_output int,
  estimated_cost numeric(12, 6),
  error_message text,
  started_at timestamptz,
  completed_at timestamptz,
  created_at timestamptz not null default now()
)

approvals (
  id uuid primary key,
  entity_type text not null,
  entity_id uuid not null,
  status text not null default 'pending',
  requested_by uuid references users(id),
  reviewed_by uuid references users(id),
  reviewer_comments text,
  requested_at timestamptz not null default now(),
  reviewed_at timestamptz,
  metadata jsonb not null default '{}'
)

integration_connections (
  id uuid primary key,
  provider text not null, -- apollo, sendgrid, microsoft_graph, whatsapp, make
  status text not null default 'disconnected',
  config jsonb not null default '{}',
  secret_ref text,
  last_tested_at timestamptz,
  last_error text,
  created_at timestamptz not null default now(),
  updated_at timestamptz not null default now()
)

webhook_events (
  id uuid primary key,
  provider text not null,
  event_type text,
  external_event_id text,
  payload jsonb not null,
  processed_status text not null default 'pending',
  error_message text,
  received_at timestamptz not null default now(),
  processed_at timestamptz
)

audit_logs (
  id uuid primary key,
  actor_type text not null,
  actor_id uuid,
  action text not null,
  entity_type text,
  entity_id uuid,
  before_state jsonb,
  after_state jsonb,
  metadata jsonb not null default '{}',
  created_at timestamptz not null default now()
)
```

Recommended indexes:

```sql
create index idx_agent_runs_agent_status on agent_runs(agent_definition_id, status, created_at desc);
create index idx_approvals_entity on approvals(entity_type, entity_id, status);
create index idx_webhook_events_provider_status on webhook_events(provider, processed_status, received_at);
create index idx_audit_logs_entity on audit_logs(entity_type, entity_id, created_at desc);
```

---

## 6. Sprint Sequencing

Assumption: two-week sprints. If the team is small, treat each sprint as a sequencing unit rather than a strict two-week promise.

### Sprint 0: Technical Discovery And Setup

Primary outcome: engineering starts with decisions made.

Work:

- Finalize stack: Next.js, backend framework, ORM, auth approach.
- Confirm AWS account, EC2 sizing, domain/subdomain plan.
- Confirm WABA provider.
- Confirm SendGrid and Microsoft Graph access path.
- Confirm Apollo API access.
- Create repo, branching strategy, environments, CI basics.
- Finalize first three launch campaign lanes as seed data.

Exit criteria:

- Engineering can start Sprint 1 without waiting on tool choices.
- Secrets and integration ownership are assigned.

### Sprint 1: App Foundation And Growth Core

Epics:

- E01 Product Foundation.
- E02 Growth Data Core.

Stories:

- E01-US01, E01-US02, E01-US03.
- E02-US01, E02-US02, E02-US03, E02-US04.

Exit criteria:

- Users can log in.
- Roles work.
- Accounts, contacts, leads, tasks exist.
- Lead list and lead detail are usable.

### Sprint 2: Timeline, Consent, Capture, Files

Epics:

- E02 Growth Data Core.
- E03 Manual Capture.
- E17 Security foundations.

Stories:

- E02-US05, E02-US06.
- E03-US01, E03-US02.
- E17-US05.

Exit criteria:

- Personal WhatsApp/call briefs can be manually captured.
- Files upload to storage.
- Timeline and consent records exist.
- Audit logging begins.

### Sprint 3: CMO Brain Foundation

Epics:

- E04 CMO Brain And Agent Ops.

Stories:

- E04-US01, E04-US02, E04-US03, E04-US04.

Exit criteria:

- Lead scoring and offer/pillar recommendation works.
- Agent registry and run logs are visible.
- AI outputs are explainable and linked to records.

### Sprint 4: Approval Queue And Apollo

Epics:

- E04 CMO Brain.
- E05 Apollo.

Stories:

- E04-US05.
- E05-US01, E05-US02, E05-US03.

Exit criteria:

- AI outputs can be approved/rejected/revised.
- Apollo prospects can be imported.
- Leads can be enriched.

### Sprint 5: LinkedIn Workbench

Epics:

- E06 LinkedIn Workbench.

Stories:

- E06-US01, E06-US02, E06-US03, E06-US04, E06-US05.

Exit criteria:

- LinkedIn prospects can be manually added.
- Operator has a daily queue.
- Suggested copy exists.
- Outcomes create timeline entries and warm signals.
- No LinkedIn automation or scraping exists.

### Sprint 6: Seasonal Calendar And Campaign Portfolio

Epics:

- E07 Seasonal Calendar And Campaign Portfolio.

Stories:

- E07-US01, E07-US03, E07-US04, E07-US05.
- E07-US02 if capacity allows.

Exit criteria:

- Seasonal opportunities can be created and edited.
- Campaign lanes can be created.
- Three active campaign rule is enforced.
- Campaign dashboard skeleton exists.

### Sprint 7: Landing Page Builder

Epics:

- E08 Landing Page Builder.

Stories:

- E08-US01, E08-US02, E08-US03, E08-US04, E08-US05.

Exit criteria:

- Campaign landing page can be drafted, edited, approved, published, and tracked.
- Form submissions create/update leads.
- UTM and CTA events create warm signals.

### Sprint 8: Content Studio And LinkedIn Calendar

Epics:

- E09 Content Studio.
- E10 Quality Engine.

Stories:

- E09-US01, E09-US02, E09-US03.
- E10-US01, E10-US02.

Exit criteria:

- Campaign content can be generated and reviewed.
- LinkedIn calendar supports formats and scheduling plan.
- Quality/compliance score exists.

### Sprint 9: Newsletter And Creative Production Desk

Epics:

- E09 Newsletter.
- E11 Creative Production Desk.

Stories:

- E09-US04, E09-US05.
- E11-US01, E11-US02, E11-US03.

Exit criteria:

- Monthly newsletter workflow exists.
- Creative tasks can be briefed, assigned, uploaded, and reviewed.

### Sprint 10: Asset Library And Proof Vault

Epics:

- E11 Asset Library.

Stories:

- E11-US04, E11-US05.

Exit criteria:

- Approved assets and proof assets can be stored, tagged, searched, and reused.
- Permission status protects internal-only proof.

### Sprint 11: Email Sending And SendGrid Events

Epics:

- E12 Email Campaigns.
- E15 Warm Signals.

Stories:

- E12-US01, E12-US02, E12-US03, E12-US04.
- E15-US01.

Exit criteria:

- Approved email sequences can be sent.
- SendGrid events sync back.
- Opens/clicks/bounces/unsubscribes update lead state and signals.

### Sprint 12: Outlook Reply Intelligence

Epics:

- E13 Outlook Reply Intelligence.
- E15 Lead Scoring.

Stories:

- E13-US01, E13-US02, E13-US03, E13-US04.
- E15-US02, E15-US03.

Exit criteria:

- Outlook replies from campaigns are detected, classified, summarized, and converted into tasks.
- Lead score/stage updates from replies.

### Sprint 13: WhatsApp AI Sales Assistant

Epics:

- E14 WhatsApp AI Sales Assistant.
- E15 Task Automation.

Stories:

- E14-US01, E14-US02, E14-US03, E14-US04, E14-US05.
- E15-US04.

Exit criteria:

- WABA inbound replies enter the system.
- Assistant handles approved first-level replies.
- Handoff works for high-intent or risky cases.
- Opt-out handling works.

### Sprint 14: Analytics, Weekly CMO Report, Production Hardening

Epics:

- E16 Analytics.
- E17 Deployment/Security/Observability.

Stories:

- E16-US01, E16-US02, E16-US03, E16-US04.
- E17-US01, E17-US02, E17-US03, E17-US04.

Exit criteria:

- Weekly CMO report works.
- Campaign/source/channel dashboards exist.
- Production EC2 stack is deployed.
- Backups, logs, SSL, and runbook exist.

### Sprint 15: Launch Stabilization

Primary outcome: V1 launch readiness.

Work:

- End-to-end regression testing.
- Seed first active campaign lanes.
- Test Apollo to lead to CMO score to content to landing page to outreach to reply to task flow.
- Test email unsubscribe and WhatsApp opt-out.
- Test role restrictions.
- Test backup restore.
- Fix launch blockers.

Exit criteria:

- V1 acceptance criteria from PRD are met.
- Founder can run weekly operating loop from the console.
- First three campaign lanes can be operated without engineering intervention.

---

## 7. Critical Dependencies

External dependencies:

- OpenAI API key and budget limit.
- Apollo API access and plan clarity.
- SendGrid account, sending domain, and webhook setup.
- Microsoft Azure app registration and Graph permissions.
- WhatsApp Business API provider credentials and webhook access.
- AWS account, EC2, S3, domain/subdomain, SSL.
- Initial Zlicc asset/proof inventory.
- First seed prospect lists and existing customer CSV.

Internal dependencies:

- Final role list and users.
- Approval owner for public content.
- Initial campaign lanes.
- Zlicc offer and pillar seed data.
- Content tone and compliance rules.
- WhatsApp approved templates.
- Email sender/reply-to identity.

---

## 8. V1 Launch Test Scenarios

### Scenario 1: Manual Brief Capture To Follow-Up

1. User captures a lead from personal WhatsApp notes.
2. File is uploaded.
3. CMO Brain scores lead and recommends offer.
4. Follow-up task is created.
5. Timeline shows capture, file, score, and task.

### Scenario 2: Apollo Prospect To Campaign

1. User imports Apollo prospects.
2. System deduplicates and creates leads.
3. CMO Brain scores them.
4. Campaign lane is assigned.
5. Email/LinkedIn/WhatsApp next actions are recommended.

### Scenario 3: LinkedIn Human-In-Loop

1. User adds LinkedIn prospect URL manually.
2. Operator receives task.
3. Operator copies suggested comment or DM and performs action manually.
4. Operator logs outcome.
5. Warm signal and follow-up task are created.

### Scenario 4: Landing Page Conversion

1. Campaign landing page is generated and approved.
2. Page is published.
3. Prospect submits form.
4. Lead is created/updated.
5. Warm signal and task are created.

### Scenario 5: Email Reply Intelligence

1. Approved SendGrid sequence is sent.
2. Prospect replies to Outlook reply-to.
3. Graph integration detects reply.
4. Reply Intelligence Agent classifies it.
5. Lead score, stage, and task update.

### Scenario 6: WhatsApp Handoff

1. Prospect replies to WABA campaign.
2. WhatsApp Assistant answers approved basic query.
3. Prospect asks for pricing/proposal.
4. Bot triggers handoff.
5. Sales task appears as urgent.

### Scenario 7: Creative Production

1. Campaign needs carousel/video.
2. Creative Briefing Agent creates brief.
3. Designer/editor uploads asset.
4. Reviewer requests revision.
5. Revised asset is approved and stored in asset library.

### Scenario 8: Weekly CMO Operating Loop

1. Monday report reviews active lanes.
2. CMO Brain recommends changes.
3. User approves portfolio.
4. Tuesday/Wednesday batches run.
5. Friday report shows performance and next recommendations.

---

## 9. Suggested Release Strategy

### Internal Alpha

Target after Sprint 6.

Includes:

- Auth.
- Growth data core.
- Quick capture.
- CMO scoring.
- Apollo enrichment.
- LinkedIn workbench.
- Seasonal/campaign portfolio basics.

Purpose:

- Start using the system for real prospecting even before outreach automation is complete.

### Private Beta

Target after Sprint 10.

Includes:

- Landing pages.
- Content Studio.
- Quality Engine.
- Creative Production Desk.
- Proof Vault.

Purpose:

- Run campaigns with human-managed outreach while content and page workflows mature.

### V1 Launch Candidate

Target after Sprint 14.

Includes:

- Email.
- Outlook reply intelligence.
- WhatsApp assistant.
- Warm signals.
- Analytics.
- Production deployment.

Purpose:

- Operate the full growth loop.

### V1 Launch

Target after Sprint 15 stabilization.

Includes:

- Seed campaigns live.
- Team trained.
- Runbook ready.
- Monitoring and backups verified.

---

## 10. Immediate Engineering Next Steps

1. Confirm technical stack.
2. Create repository and base app.
3. Finalize schema with engineering constraints.
4. Decide auth approach.
5. Create seed data for roles, pillars, offers, and templates.
6. Confirm integration credentials and sandbox access.
7. Start Sprint 0 discovery.

