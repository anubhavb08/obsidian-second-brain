# Zlicc Growth Console V1 PRD

Version: 0.1  
Created: 2026-05-21  
Status: Product requirements draft  
Related documents: `Zlicc_CMO_Brain.md`, `Zlicc_Growth_Console_Architecture.md`

---

## 1. Product Intent

Zlicc Growth Console is a pre-CRM prospecting, demand generation, campaign planning, content, outreach, and warm-signal intelligence platform for Zlicc.

It is not intended to replace Bigin by Zoho CRM in V1. Bigin remains the customer lifecycle CRM for deeper sales engagement, proposals, opportunities, and account management. Growth Console owns the upstream growth engine:

- Finding the right audiences.
- Creating targeted campaign lanes.
- Turning Zlicc's pillars into sellable offers.
- Generating and approving content.
- Managing LinkedIn-assisted prospecting.
- Running email and WhatsApp communication where compliant.
- Capturing replies, signals, and handoffs.
- Scoring leads and deciding the next-best action.
- Handing qualified leads into the sales/customer lifecycle process.

The product should help Zlicc run multiple targeted growth campaigns in parallel without losing clarity, quality, or follow-up discipline.

---

## 2. Strategic Position

Growth Console should act like a CMO command system, not a generic sales database.

The core CMO Brain questions are:

1. Which audience should Zlicc pursue now?
2. Which seasonal, industry, or event trigger makes this urgent?
3. Which Zlicc offer and pillar stack should be positioned?
4. Which content and landing page will make the conversation easier?
5. Which prospects should be contacted through which channel?
6. Which replies and warm signals require immediate human action?
7. Which campaign should be paused, improved, or scaled?

The product should convert Zlicc's many capabilities into focused campaign lanes, each with its own audience, offer, content, landing page, outreach flow, and performance dashboard.

---

## 3. V1 Scope

V1 focuses on aggressive prospecting and lead generation, while retaining enough nurture and expansion capability to engage known customers and agency relationships.

### In Scope

- Growth database core for accounts, contacts, leads, campaigns, tasks, notes, assets, and warm signals.
- Manual quick capture form for personal WhatsApp briefs, calls, referrals, and informal leads.
- Manual LinkedIn prospect capture and operator task workspace.
- Apollo.io based prospect search, import, and enrichment.
- CMO Brain service powered by OpenAI API.
- Specialist agent operations layer.
- Campaign portfolio scheduler with a maximum of three active campaign lanes.
- Seasonal Opportunity Calendar with AI suggestions and manual Zlicc overrides.
- Native landing page builder and publisher.
- Content Studio for LinkedIn, email, WhatsApp, scripts, carousels, articles, newsletters, decks, and briefs.
- Creative Production Desk for designers, editors, and content operators.
- LinkedIn Publishing Calendar.
- WhatsApp Business API assistant for approved replies, qualification, and human handoff.
- SendGrid or equivalent email platform for campaign sending.
- Microsoft 365 Outlook/Graph integration for reply intelligence.
- Warm signal scoring across email, Outlook, WhatsApp, landing pages, downloads, and manually logged LinkedIn activity.
- Existing customer expansion segments.
- Agency partner prospecting segments.
- Proof Vault Lite for reusable event assets and evidence.
- Analytics dashboard and weekly CMO report.
- AWS deployment on a production-style single EC2 setup.

### Out of Scope For V1

- Replacing Bigin as the full CRM.
- Automated LinkedIn scraping, auto-connection, auto-commenting, or auto-DM.
- Reading or automating personal WhatsApp or WhatsApp Business mobile app conversations.
- Fully automated public publishing without approval.
- Full proposal management.
- Full case study engine.
- Full partner/vendor operations database.
- Automated pricing, proposal promises, or delivery commitments.
- Deep Bigin integration beyond future planning.

---

## 4. Success Metrics

The system is successful if it improves campaign discipline and produces more qualified conversations.

Primary success metrics:

- Number of active campaign lanes managed without confusion.
- Number of qualified prospects created per week.
- Percentage of prospects enriched with usable email, phone, role, and company data.
- Reply rate by campaign, audience, and channel.
- Meetings booked from campaign activity.
- Warm signals captured and acted on within 24 hours.
- LinkedIn operator task completion rate.
- Landing page conversion rate.
- WhatsApp bot handoff quality and speed.
- Content approval cycle time.
- Creative task turnaround time.
- Number of existing customers engaged for cross-sell or upsell education.
- Weekly CMO report quality and usefulness.

Guardrail metrics:

- Opt-out compliance.
- Bounce rate and email reputation signals.
- Unapproved claims blocked.
- Client reference violations blocked.
- WhatsApp conversations escalated when needed.
- Human approvals completed before public publishing or campaign activation.

---

## 5. User Roles

### Founder / Marketing Owner

Primary decision-maker. Reviews CMO Brain recommendations, approves campaign lanes, approves public content, reviews hot replies, and decides business priorities.

Permissions:

- Full access.
- Approve, edit, pause, or reject campaigns.
- Approve landing pages, LinkedIn posts, newsletters, WhatsApp templates, email sequences, and key claims.
- View analytics and agent outputs.
- Override seasonal calendar entries and campaign priorities.

### Admin

Manages settings, users, integrations, permissions, API keys, templates, and system configuration.

Permissions:

- Full configuration access.
- API/integration management.
- User and role management.
- Data import/export.

### CMO Brain

AI orchestration layer inside the Growth Console application.

Responsibilities:

- Prioritize campaign lanes.
- Review specialist agent outputs.
- Score leads and recommend next-best actions.
- Recommend offers, pillars, content, landing pages, and channels.
- Audit campaign performance and recommend improvements.

Approval limits:

- Cannot publish, send sensitive communication, activate campaigns, approve pricing, or use client references without human approval.

### LinkedIn Operator

Executes LinkedIn tasks manually from an assigned queue.

Permissions:

- View assigned prospects.
- Open profile links.
- View suggested comments, connection notes, and DMs.
- Mark tasks done, skipped, snoozed, connected, replied, or not relevant.
- Add response summaries and notes.

Restrictions:

- Cannot change CMO recommendations or lead scores.
- Cannot send WhatsApp or email campaigns.
- Cannot edit strategy, prompts, integrations, or API keys.
- Cannot delete leads.

### Creative Team Member

Designers, video editors, content operators, or production collaborators who execute creative tasks.

Permissions:

- View assigned production tasks.
- View briefs, references, formats, copy, and due dates.
- Upload source files, exports, thumbnails, and notes.
- Respond to review comments.

Restrictions:

- Cannot activate campaigns.
- Cannot approve final assets unless granted reviewer permission.
- Cannot access sensitive integration settings.

### Sales / Handoff Owner

Receives high-intent replies, WhatsApp bot escalations, meeting requests, and proposal requests.

Permissions:

- View assigned hot leads and conversation summaries.
- Add notes and follow-up status.
- Mark meeting booked, proposal requested, nurture, not relevant, or lost.
- Trigger handoff to Bigin manually in V1 if needed.

---

## 6. Core Product Modules

### 6.1 Growth Data Core

The database foundation for all growth workflows.

Required entities:

- Accounts.
- Contacts.
- Leads.
- Campaigns.
- Campaign lanes.
- Tasks.
- Notes.
- Interactions.
- Manual captures.
- LinkedIn prospect captures.
- Outreach messages.
- Landing pages.
- Content assets.
- Production tasks.
- Proof assets.
- Consent records.
- Warm signals.
- Agent runs.

Core requirements:

- Every lead must have a source.
- Every lead should have a stage, score, recommended offer, recommended pillar stack, and next-best action.
- Every interaction should be tied to a contact, lead, campaign, and channel where possible.
- Every campaign should be tied to an audience, offer, landing page, content set, outreach sequence, and performance report.
- Consent, unsubscribe, opt-out, and suppression data must be available before outreach.

### 6.2 Manual Quick Capture

Used when the founder or team receives briefs or lead details through personal WhatsApp, calls, referrals, or informal discussions.

Minimum fields:

- Contact name.
- Company name.
- Mobile/WhatsApp number.
- Email, optional.
- LinkedIn URL, optional.
- Source.
- Brief notes.
- Required solution or event type, optional.
- Files or links.
- Next follow-up date, optional.

Behavior:

- If contact/company exists, append the note and files.
- If not, create account, contact, lead, and opportunity draft.
- CMO Brain classifies the lead, recommends offer/pillars, scores it, and creates a follow-up task.
- No personal WhatsApp inbox reading or scraping is allowed.

### 6.3 Prospecting And Apollo Enrichment

Apollo should be the structured prospecting and enrichment engine.

Requirements:

- Import prospects from Apollo based on selected filters.
- Support filters such as company category, industry, role, seniority, geography, company size, and campaign context where available.
- Enrich manually captured leads and LinkedIn prospects.
- Store enrichment source, timestamp, confidence, and fields returned.
- Deduplicate contacts and companies before import.
- Mark records as enrichment pending, enriched, failed, or needs manual review.

### 6.4 LinkedIn Workbench

LinkedIn remains human-in-loop.

Requirements:

- Add LinkedIn Prospect form.
- Store profile URL, relationship source, notes, priority, campaign tag, and owner.
- Generate suggested comment, connection note, first DM, and follow-up DM.
- Assign tasks to LinkedIn Operator.
- Provide Today, Overdue, High Priority, Replied, and Snoozed queues.
- Log manual outcomes.
- Convert positive LinkedIn outcomes into email/WhatsApp/call follow-up tasks where appropriate.

Prohibited behavior:

- No scraping.
- No automated connection requests.
- No automated comments.
- No automated DMs.
- No automated extraction from LinkedIn pages unless an approved API is used.

### 6.5 CMO Brain

The CMO Brain resides inside the Growth Console backend as an AI service using OpenAI API.

Inputs:

- CMO Brain document.
- Zlicc pillar definitions.
- Offer library.
- Campaign performance data.
- Lead profile and interaction history.
- Seasonal calendar entries.
- Asset library and proof metadata.
- Compliance and approval rules.

Outputs:

- Lead classification.
- Lead score and reason.
- Recommended offer and pillar stack.
- Next-best action.
- Campaign lane recommendation.
- Content brief.
- Landing page brief.
- Outreach drafts.
- Creative production brief.
- Reply classification.
- Weekly performance summary.

Approval rules:

- CMO Brain can recommend and draft.
- CMO Brain cannot activate, publish, or send sensitive public-facing content without approval.
- Human approval is mandatory for public posts, campaigns, newsletters, landing pages, pricing, proposals, client references, and high-value prospects.

### 6.6 Agent Operations Layer

The system should use specialist agents under the CMO Brain.

V1 specialist agents:

- Market Research Agent.
- Prospecting Agent.
- Content Strategy Agent.
- Creative Briefing Agent.
- WhatsApp Sales Assistant.
- Reply Intelligence Agent.
- Analytics Agent.
- Compliance and Guardrails Agent.

Each agent record must include:

- Purpose.
- Allowed inputs.
- Allowed tools.
- Output type.
- Approval requirement.
- Escalation rules.
- Last run.
- Run logs.
- Quality score.
- Error state.

Agent hierarchy:

- Specialist agents research, draft, classify, score, summarize, and prepare outputs.
- CMO Brain reviews, prioritizes, audits, approves, redirects, pauses, and analyzes.
- Humans approve sensitive or public actions.

### 6.7 Campaign Portfolio Scheduler

The system should support multiple campaign lanes in parallel.

Rules:

- Maximum three active campaign lanes at one time.
- Up to two aggressive prospecting campaigns.
- Up to one nurture, education, existing customer, or agency relationship campaign.
- Other campaigns stay draft, scheduled, paused, completed, or archived.

Campaign lane fields:

- Campaign name.
- Seasonal trigger.
- Target audience.
- Target roles.
- Prospect list.
- Offer.
- Pillar stack.
- Landing page.
- Content set.
- LinkedIn publishing plan.
- Outreach sequence.
- Creative tasks.
- Owner.
- Priority.
- Status.
- Metrics.

Important:

- AGM, Global Fintech Fest, exhibitions, festivals, and similar examples are seed references only.
- Campaign opportunities must not be hard-coded.
- Market Research Agent should refresh and recommend opportunities using current market context, available sources, and manual Zlicc knowledge.

### 6.8 Seasonal Opportunity Calendar

An editable calendar that combines AI-assisted market timing and Zlicc's internal experience.

Fields:

- Name.
- Category.
- Planning window.
- Event window.
- Audience.
- Industries.
- Recommended offer.
- Relevant pillars.
- Priority.
- Source.
- Notes.
- Repeat yearly.
- Reminder schedule.
- Linked campaign.
- Linked landing page.

Requirements:

- AI can suggest seasonal opportunities.
- Users can add, edit, override, and archive opportunities.
- Manual Zlicc entries override generic AI assumptions.
- Support reminders 90, 60, 45, and 30 days before relevant planning windows.
- Calendar entries can generate recommended campaign lanes.

### 6.9 Landing Page Builder

Landing pages should be generated and published from within the Growth Console. Manual HTML uploads should not be required for normal campaigns.

V1 requirements:

- Native hosted landing pages on a Zlicc-controlled domain or subdomain.
- Fixed premium templates.
- Click-to-publish workflow.
- Editable content before publishing.
- Lead capture forms.
- Download gates for decks/one-pagers where needed.
- WhatsApp CTA.
- UTM tracking.
- Campaign attribution.
- Form submission to Growth Data Core.
- Warm-signal creation for visits, form fills, downloads, and CTA clicks.

V1 template types:

- Agency Tech Partner.
- ZliccPulse Activity Menu.
- AI Event Experience Kit.
- Exhibition Booth Intelligence.
- Hybrid AGM/Webcast.
- Product Launch Experience.
- Existing Customer Expansion.

Editable sections:

- Headline.
- Subheadline.
- Problem.
- Offer.
- Pillar stack.
- Use cases.
- Proof/assets.
- Downloadable deck.
- WhatsApp CTA.
- Lead form.
- UTM tags.

Future optional integrations:

- Webflow publish/sync.
- Main Zlicc website publishing.
- HTML export.

### 6.10 Content Studio

Content Studio turns campaign strategy into channel-specific content.

Supported formats:

- LinkedIn company page posts.
- Founder/profile post drafts.
- Text POV posts.
- Document/carousel outlines.
- Polls.
- Short video scripts.
- Proof/image posts.
- Articles.
- LinkedIn newsletters.
- Email newsletters.
- Email sequences.
- WhatsApp messages.
- Deck and one-pager outlines.
- Image prompts and creative references.

Requirements:

- Content must always be generated from campaign context, not random prompts.
- Every draft must store campaign, audience, offer, pillar stack, CTA, intended channel, approval status, and quality score.
- Content can be revised through Quality Engine.
- Approved content is stored in the asset library.
- Public content needs human approval.

LinkedIn cadence:

- Company page: three posts per week.
- Founder/profile drafts: two to three posts per week.
- Carousel/document: one per week.
- Short video: one per week when production capacity allows.
- Poll: one to two per month.
- Article: one per month.
- Newsletter: one per month.

Recommended weekly rhythm:

- Tuesday: primary campaign post or carousel plus approved outreach batch.
- Wednesday: second campaign post, short video/proof post, or second approved outreach batch.
- Thursday: follow-ups, LinkedIn engagement, warm-signal review, and WhatsApp handoffs.
- Saturday: optional lighter post, poll, recap, behind-the-scenes, or visual showcase.

### 6.11 Newsletter Engine

Newsletter should be part of V1, but with a controlled cadence.

Requirements:

- Support LinkedIn newsletter planning.
- Support email newsletter planning for warm leads, existing customers, agencies, and opted-in contacts.
- Monthly cadence by default.
- Repurpose strong campaign insights, proof assets, LinkedIn posts, and seasonal opportunities.
- Require approval before publishing or sending.

### 6.12 Creative Production Desk

This is the bridge between AI-generated context and human-produced final assets.

Requirements:

- CMO Brain and Creative Briefing Agent generate production briefs.
- Designers/editors receive tasks inside the system.
- Tasks include audience, offer, copy/script, references, format, size, duration, deadline, priority, and quality checklist.
- Team members upload source files, final exports, thumbnails, notes, and versions.
- Reviewers can comment, request changes, approve, or archive.
- Approved assets move into the asset library.

Production task fields:

- Campaign.
- Lead, optional.
- Offer.
- Zlicc pillar.
- Asset type.
- Assigned owner.
- Creative brief.
- Copy/script.
- References.
- Format.
- Size/duration.
- Deadline.
- Priority.
- Status.
- Uploads.
- Version history.
- Quality score.
- Reviewer comments.

### 6.13 Content Quality Engine

The Quality Engine protects Zlicc from generic, weak, off-brand, risky, or inaccurate content.

Scorecard dimensions:

- Strategic relevance.
- Audience specificity.
- Zlicc pillar accuracy.
- Offer clarity.
- Proof strength.
- CTA clarity.
- Tone and brand fit.
- Visual brief quality.
- Channel fit.
- Compliance and claims safety.

Requirements:

- Drafts below quality threshold should be revised before approval.
- Claims, client references, pricing, and capability statements should be checked.
- Low-confidence or high-risk outputs should be routed to human review.
- Final public-facing content needs human approval.

### 6.14 WhatsApp AI Sales Assistant

The assistant operates only on WhatsApp Business API conversations, not personal WhatsApp or the mobile app inbox.

Capabilities:

- Respond to approved campaign replies.
- Share approved details, landing page links, and deck links.
- Ask qualifying questions.
- Classify intent.
- Update lead status and score.
- Create human handoff tasks.
- Handle opt-out or not interested intent.

Qualification fields:

- Company.
- Requirement.
- Event type.
- Timeline.
- Expected audience.
- Interest area.
- Budget range, only if appropriate and approved.
- Meeting/call preference.

Human handoff triggers:

- Pricing.
- Proposal.
- Meeting request.
- Complex brief.
- Negative sentiment.
- Low confidence.
- Repeated back-and-forth.
- High lead score.
- Named strategic account.

### 6.15 Email Campaigns And Outlook Reply Intelligence

SendGrid or equivalent should handle campaign sending. Microsoft 365 Outlook is used for reply intelligence, not bulk sending.

Requirements:

- Create and approve email sequences.
- Send campaigns through SendGrid or selected email platform.
- Track sent, delivered, bounced, opened, clicked, unsubscribed, and replied where available.
- Set reply-to as the founder/user Outlook mailbox where required.
- Use Microsoft Graph to detect relevant replies in Outlook.
- Classify reply intent.
- Update lead score and stage.
- Create follow-up tasks.

Reply categories:

- Interested.
- Meeting requested.
- Send details.
- Proposal requested.
- Not now.
- Not relevant.
- Wrong person.
- Referral to another person.
- Unsubscribe/remove.
- Negative sentiment.
- Out of office.

### 6.16 Warm Signal Tracking

Warm signals should drive lead score and urgency.

Signal sources:

- SendGrid opens and clicks.
- Outlook replies.
- WhatsApp replies.
- WhatsApp bot qualification.
- Landing page visits.
- Form fills.
- Deck downloads.
- WhatsApp CTA clicks.
- LinkedIn manual logs.
- Meeting booked.
- Creative/proof engagement where trackable.

Requirements:

- Every signal should store source, timestamp, campaign, lead/contact, score delta, and reason.
- High-value signals should create tasks.
- Repeated low-value signals should trigger nurture recommendations.
- Negative signals should trigger suppression, pause, or lower score where appropriate.

### 6.17 Existing Customer Expansion

V1 should support uploading and segmenting known contacts and companies.

Requirements:

- Import contacts and companies.
- Tag by past project, industry, relationship strength, likely next offer, and permission status.
- Create education, cross-sell, and upsell campaigns.
- Avoid treating existing customers like cold prospects.
- Surface likely expansion opportunities to CMO Brain.

### 6.18 Agency Partner Thread

Agencies should have a dedicated prospecting track.

Requirements:

- Segment event, experiential, exhibition, creative, production, and MICE agencies.
- Track agency type, sectors served, partnership potential, likely Zlicc stack, and repeat opportunity potential.
- Generate agency-specific collateral and outreach.
- Create LinkedIn and email/WhatsApp workflows suited to agency partnerships.

### 6.19 Proof Vault Lite

Proof Vault Lite provides campaign evidence without building the full case study engine yet.

Requirements:

- Upload event photos, videos, decks, recap links, campaign screenshots, and metrics.
- Tag by client, pillar, use case, industry, permission status, and public/internal visibility.
- Let CMO Brain recommend proof assets for campaigns, landing pages, and content.
- Prevent public use of assets marked internal-only or unapproved.

### 6.20 Analytics Dashboard

Analytics should help the CMO Brain and founder decide what to do next.

Dashboards:

- Campaign portfolio overview.
- Lead source performance.
- Offer performance.
- Pillar performance.
- Channel performance.
- Warm signal dashboard.
- Landing page performance.
- WhatsApp bot/handoff performance.
- LinkedIn operator performance.
- Creative production status.
- Content approval and quality trends.
- Weekly CMO report.

---

## 7. Integrations

### OpenAI API

Purpose:

- CMO Brain.
- Specialist agents.
- Lead scoring.
- Content generation.
- Reply classification.
- Quality review.
- Summaries and recommendations.

Notes:

- This uses OpenAI API billing separately from ChatGPT Pro.
- API usage should be metered by feature and agent run.
- Admin should be able to set monthly spend limits and disable non-critical runs.

### Apollo.io

Purpose:

- Prospect list building.
- Person/company enrichment.
- Email/phone discovery where available.

Requirements:

- Import selected lists.
- Enrich selected leads.
- Store source and confidence.
- Deduplicate before save.

### WhatsApp Business API Provider

Purpose:

- Approved WhatsApp templates.
- Campaign replies.
- WhatsApp AI Sales Assistant.
- Human handoff.
- Opt-out handling.

Notes:

- Existing Zlicc WABA/API setup should be used.
- Personal WhatsApp mobile app is not integrated.

### SendGrid Or Email Platform

Purpose:

- Campaign email sending.
- Event tracking.
- Unsubscribe and bounce management.

Requirements:

- Domain authentication.
- Unsubscribe support.
- Webhook event sync.
- Campaign and message metadata.

### Microsoft 365 Outlook Via Graph

Purpose:

- Read relevant inbound replies from the reply-to mailbox.
- Classify intent.
- Update lead status and score.
- Create follow-up tasks.

Notes:

- Not for bulk sending in V1.
- Requires tenant/app permissions and secure OAuth setup.

### Make

Purpose:

- Practical automation bridge for early integrations and webhook workflows.

Use cases:

- Lightweight webhook routing.
- Notification bridges.
- File/task notifications.
- Temporary integration flows while native integrations are built.

Long-term note:

- Critical workflows should gradually move into the Growth Console backend when stability and control become important.

### Asset Storage

Purpose:

- Store uploaded files, landing page media, proof assets, creative exports, and documents.

Preferred V1:

- AWS S3 for production file storage.
- Local file storage only for development.

### Bigin By Zoho CRM

Purpose:

- Not part of core V1 automation.
- Future integration to push qualified prospects, contacts, notes, and opportunities into Bigin.

V1 expectation:

- Manual handoff or export is acceptable.

---

## 8. Core Workflows

### 8.1 New Prospect From Apollo

1. User or Prospecting Agent defines target criteria.
2. Apollo returns prospect list.
3. System deduplicates accounts and contacts.
4. Leads are created with source and campaign context.
5. CMO Brain scores each lead and recommends offer/pillar stack.
6. Compliance layer checks suppression and channel eligibility.
7. Leads are assigned to campaign lane, LinkedIn task, email sequence, WhatsApp path, or nurture.

### 8.2 New Prospect From LinkedIn

1. User/operator enters LinkedIn URL and notes manually.
2. System creates or updates prospect record.
3. Apollo enrichment is triggered when enough information is available.
4. CMO Brain scores and recommends next-best action.
5. LinkedIn Operator receives manual task and suggested copy.
6. Operator completes action in LinkedIn and logs outcome.
7. Warm signal or follow-up task is created.

### 8.3 Manual Brief Capture From Personal WhatsApp Or Call

1. User opens Quick Capture.
2. User enters a few lines and uploads files/links if required.
3. System attaches data to existing record or creates new lead.
4. CMO Brain classifies need, offer fit, urgency, and next step.
5. Task is created for follow-up, deck, proposal, or meeting.

### 8.4 Campaign Lane Creation

1. Seasonal Calendar, Market Research Agent, or user creates opportunity.
2. CMO Brain recommends campaign lane.
3. User approves active, draft, scheduled, paused, or archived status.
4. Campaign Builder defines audience, offer, pillars, prospect list, landing page, content plan, outreach, LinkedIn plan, and creative tasks.
5. Content Studio and Landing Page Builder generate drafts.
6. Quality Engine checks drafts.
7. Human approves before publish/send.

### 8.5 Landing Page Publish

1. Campaign Builder sends brief to Landing Page Builder.
2. CMO Brain drafts page copy.
3. User selects fixed premium template.
4. Approved assets are attached.
5. User edits and approves.
6. Page is published under Zlicc-controlled domain/subdomain.
7. Form submissions and warm signals return to Growth Console.

### 8.6 Creative Production

1. Campaign needs asset.
2. Creative Briefing Agent generates task brief.
3. Designer/editor receives task.
4. Asset is produced in Canva, Figma, PPT, Runway, video editor, or other production tool.
5. File is uploaded to Growth Console.
6. Quality Engine and human reviewer check it.
7. Approved asset moves to Asset Library.
8. Campaign uses the asset.

### 8.7 Email Reply Intelligence

1. Email campaign is sent from SendGrid with user Outlook reply-to.
2. Prospect replies to Outlook mailbox.
3. Microsoft Graph detects relevant reply.
4. Reply Intelligence Agent classifies intent.
5. Lead score and stage are updated.
6. Follow-up task or sales handoff is created.

### 8.8 WhatsApp Bot Conversation

1. Prospect replies on WABA.
2. WhatsApp AI Sales Assistant checks approved knowledge and context.
3. Bot answers basic questions or asks qualifying questions.
4. Lead status and score are updated.
5. Human handoff is triggered when required.

### 8.9 Weekly Operating Loop

Monday:

- Specialist agents surface research, prospecting, and performance inputs.
- CMO Brain reviews campaign portfolio, seasonal windows, and capacity.
- Confirm up to three active campaign lanes.

Tuesday:

- Publish/send first priority campaign batch.
- Prepare upcoming landing pages and content.

Wednesday:

- Publish/send second campaign batch.
- Clear creative approvals.

Thursday:

- Run follow-ups, LinkedIn engagement, warm-signal review, and WhatsApp handoffs.

Friday:

- Analytics Agent reports performance by campaign lane.
- CMO Brain audits results and adjusts next week's portfolio.

Saturday:

- Optional lighter LinkedIn post, poll, recap, behind-the-scenes, or visual showcase.

---

## 9. UX Requirements

### Primary Navigation

- Today.
- Agent Ops.
- Quick Capture.
- Prospecting.
- LinkedIn Operator.
- Leads.
- Seasonal Calendar.
- Campaign Portfolio.
- Landing Pages.
- LinkedIn Publishing.
- Newsletters.
- Content Studio.
- Creative Production Desk.
- Outreach.
- Assets.
- Existing Customers.
- Analytics.
- Settings.

### Today Screen

Should answer:

- What needs approval today?
- Which leads are hot?
- Which replies need action?
- Which campaign lanes are active?
- Which LinkedIn tasks are overdue?
- Which creative tasks are blocked?
- Which WhatsApp bot conversations need handoff?
- Which landing pages or content drafts are pending approval?

### Campaign Portfolio Screen

Should show:

- Active campaign lanes.
- Draft/scheduled/paused/completed campaigns.
- Campaign priority tier.
- Target audience and offer.
- Landing page status.
- Content status.
- Outreach status.
- Warm signals.
- Meetings and replies.
- Next recommendation.

### Lead Detail Screen

Should show:

- Contact and company information.
- Source and enrichment data.
- Current score and score reasons.
- Recommended offer and pillar stack.
- Stage.
- Timeline of interactions.
- Warm signals.
- Tasks.
- LinkedIn notes.
- WhatsApp/email activity.
- Landing page activity.
- Recommended next action.

### Agent Ops Screen

Should show:

- Agent list.
- Last run.
- Status.
- Inputs.
- Outputs.
- Quality score.
- Approval requirement.
- Errors.
- Escalations.
- Re-run or approve controls.

---

## 10. Technical Architecture

### Recommended Stack

Frontend:

- Next.js or equivalent React framework.
- Role-based dashboard UI.
- Responsive admin and operator views.

Backend:

- Node.js/NestJS or equivalent structured API framework.
- REST or GraphQL API.
- Worker process for agent jobs, webhook processing, enrichment, scoring, and scheduled jobs.

Database:

- PostgreSQL.

Queue/cache:

- Redis.

Storage:

- AWS S3.

AI:

- OpenAI API.
- Prompt/config versioning for CMO Brain and agents.

Automation bridge:

- Make for early webhook and integration workflows where useful.

Deployment:

- AWS EC2.
- Docker Compose.
- Nginx reverse proxy.
- SSL via Let's Encrypt.
- CloudWatch or lightweight logging.
- Daily PostgreSQL backups to S3.

### V1 EC2 Services

Docker Compose should run:

- `web`: frontend.
- `api`: backend API.
- `worker`: background jobs and agent runs.
- `postgres`: database.
- `redis`: queue/cache.
- `nginx`: reverse proxy.

Optional:

- `adminer` or similar database tool, restricted to admin access only.
- `prometheus/grafana` later if monitoring needs grow.

### Environments

Required environments:

- Local development.
- Staging.
- Production.

At minimum, production should not share secrets or database with development.

---

## 11. Security And Compliance

Requirements:

- Role-based access control.
- Secure API key storage.
- OAuth for Microsoft Graph.
- Webhook signature validation where supported.
- Audit log for approvals, sends, agent outputs, and sensitive changes.
- Consent and opt-out records.
- Unsubscribe handling for email.
- WhatsApp opt-out handling.
- Suppression list.
- Client reference permission tags.
- Internal-only asset protection.
- Human approval before public publishing.
- Human approval before sensitive claims, pricing, proposals, and client references.

Data retention:

- Store only required data.
- Allow deletion or suppression of contacts where required.
- Keep audit logs for important sends, approvals, and opt-outs.

---

## 12. Development Roadmap

### Phase 1: Product Foundation

Deliver:

- App shell and authentication.
- Roles and permissions.
- Growth Data Core.
- Accounts, contacts, leads, tasks, notes.
- Quick Capture form.
- LinkedIn Prospect form.
- Basic lead detail and lead list.

Acceptance:

- User can create/import leads.
- User can manually capture WhatsApp/call/referral briefs.
- System can store source, notes, files, and follow-up tasks.

### Phase 2: CMO Brain And Agent Ops

Deliver:

- CMO Brain service.
- Prompt/config loading from CMO Brain document.
- Agent registry.
- Lead scoring.
- Offer/pillar recommendation.
- Next-best action.
- Agent run logs.

Acceptance:

- Lead can be scored and classified.
- CMO Brain can explain recommendations.
- Agent outputs are visible and auditable.

### Phase 3: Prospecting And LinkedIn Workbench

Deliver:

- Apollo import/enrichment.
- Deduplication.
- LinkedIn Operator workspace.
- Suggested LinkedIn copy.
- Manual completion logging.

Acceptance:

- Apollo prospects can become leads.
- LinkedIn URL captures can be enriched and assigned.
- Operator can work daily queue and log outcomes.

### Phase 4: Campaign Portfolio And Seasonal Calendar

Deliver:

- Editable Seasonal Opportunity Calendar.
- AI/manual opportunity entries.
- Campaign Portfolio Scheduler.
- Campaign lane builder.
- Up to three active lanes.

Acceptance:

- User can create opportunities manually.
- CMO Brain can recommend campaign lanes.
- System enforces active campaign lane limit.

### Phase 5: Landing Pages And Content Studio

Deliver:

- Native landing page templates.
- Draft, edit, approve, publish workflow.
- Content Studio drafts.
- LinkedIn Publishing Calendar.
- Newsletter planning.
- Quality scorecard.

Acceptance:

- Campaign can generate landing page and content drafts.
- User can approve and publish a landing page.
- LinkedIn and newsletter drafts can be planned and approved.

### Phase 6: Outreach And Reply Intelligence

Deliver:

- SendGrid integration.
- Microsoft Graph reply intelligence.
- WhatsApp Business API integration.
- WhatsApp AI Sales Assistant.
- Opt-out handling.
- Warm signal tracking.

Acceptance:

- Email events sync to leads.
- Outlook replies update lead status and tasks.
- WABA replies can be classified and routed.
- WhatsApp bot escalates correctly.

### Phase 7: Creative Production Desk And Proof Vault

Deliver:

- Production task buckets.
- Creative briefs.
- Uploads and version history.
- Review comments.
- Asset approval.
- Proof Vault Lite.

Acceptance:

- Designer/editor can receive task, upload output, and get revision comments.
- Approved assets can be used in campaigns and landing pages.
- Proof assets respect permission status.

### Phase 8: Analytics And Weekly Operating Loop

Deliver:

- Campaign dashboards.
- Channel dashboards.
- Warm signal dashboard.
- Creative production dashboard.
- Weekly CMO report.

Acceptance:

- User can see which campaigns are working.
- CMO Brain can recommend next week's adjustments.
- Reports include replies, meetings, content status, landing page performance, and warm signals.

---

## 13. Acceptance Criteria For V1 Launch

V1 can be considered ready when:

- The founder can manage up to three active campaign lanes.
- A prospect can enter from Apollo, LinkedIn manual capture, existing customer import, landing page, or quick capture.
- Leads can be scored, classified, and assigned a recommended Zlicc offer.
- The system can generate campaign content, outreach drafts, landing page copy, and creative briefs from campaign context.
- A landing page can be published from the app without manual HTML upload.
- LinkedIn remains human-in-loop with an operator queue and logging.
- Email campaigns can be sent through SendGrid or selected platform.
- Outlook replies can be classified and converted into lead updates/tasks.
- WhatsApp Business API replies can be handled by approved bot logic with human handoff.
- Designers/editors can receive production tasks and upload final assets.
- Warm signals update lead score and urgency.
- Content quality and compliance checks block weak or risky outputs.
- Weekly analytics can tell which campaign lanes should continue, pause, or improve.

---

## 14. Key Product Principles

- Campaigns are not one-size-fits-all.
- Do not market Zlicc pillars as isolated features; market the business moment they make possible.
- Examples like AGM, exhibitions, fintech events, and festive activations are campaign seeds, not hard-coded rules.
- Manual Zlicc experience is a first-class input.
- AI should create leverage, not remove judgment.
- LinkedIn must stay human-led.
- Personal WhatsApp must stay manual.
- SendGrid handles campaigns; Outlook handles reply intelligence.
- Bigin remains lifecycle CRM in V1.
- Creative quality depends on human production with AI-powered context and review.
- The CMO Brain should review, audit, approve, prioritize, and analyze, while specialist agents do focused work.

---

## 15. Open Decisions

These should be finalized before engineering starts:

1. Exact frontend/backend stack.
2. Preferred WhatsApp Business API provider details.
3. SendGrid versus alternate email platform.
4. Apollo plan and API access level.
5. Microsoft Graph tenant permissions and app registration approach.
6. Zlicc subdomain for landing pages.
7. Initial user list and role assignments.
8. First three campaign lanes to configure after launch.
9. Whether Make is used only for interim automation or also for selected long-term workflows.
10. Whether Bigin export is manual CSV in V1 or a small one-click handoff.

---

## 16. V2 Backlog

Do not build these before the V1 prospecting engine is stable:

- Referral Engine.
- Competitor and Market Intelligence.
- Full Proof and Case Study Engine.
- Partner and Vendor Ecosystem.
- Delivery Capacity Check.
- Win/Loss Intelligence.
- Native Bigin integration.
- Webflow/main website publishing integration.
- Advanced marketing attribution.
- Advanced capacity planning for creative and delivery teams.
- Multi-brand or multi-business-unit support.

