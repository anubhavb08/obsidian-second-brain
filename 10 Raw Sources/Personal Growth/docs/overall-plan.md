# Growth Automation Studio: Overall Plan

## Working Name

The working market-facing product name is **Zandem.ai**.

Growth Automation Studio remains the internal architecture and business descriptor while the brand is still provisional.

## Positioning

Zandem.ai is a managed B2B pre-CRM growth system. It helps clients move from scattered outreach and ad hoc content into a structured growth operating layer:

Client Brain -> Campaign Lanes -> AI Campaign Assets -> Outreach Workflows -> Warm Signals -> Qualified Conversation Handoff.

The promise is not generic marketing automation. The promise is a repeatable system for creating campaigns, generating assets, running approved outreach workflows, and surfacing qualified conversations.

## Target Customer

V1 is designed for B2B companies that need customer acquisition but do not have a mature internal growth-ops, creative, and outbound automation function.

Primary early fit:

- Founder-led B2B companies.
- B2B service businesses.
- B2B product or platform companies with clear target accounts.
- Mid-market teams that want custom deployment instead of generic SaaS setup.

## Deployment Model

V1 should be sold and delivered as a managed single-client deployment.

The first deployment should produce:

- Client Brain configuration.
- Brand kit and proof library.
- 2-3 campaign lanes.
- AI-generated campaign kit.
- Email, LinkedIn, and WhatsApp operating rules.
- Warm-signal and lead-scoring logic.
- CRM or sales handoff workflow.
- Weekly or fortnightly AI CMO review rhythm.
- Weekly reporting and action-plan rhythm.

Commercial structure, retainer credits, and third-party service usage are intentionally left for a later pricing exercise.

## Product Modules

### Client Brain

Stores the client's ICPs, offers, positioning, proof assets, tone, brand rules, claim boundaries, compliance rules, approval rules, and CRM handoff logic.

### Campaign Factory

Turns Client Brain and market research into 2-3 active campaign lanes. Each lane has an audience, offer, CTA, channel mix, assets, outreach path, KPI targets, and decision status.

### AI Creative Studio

Generates campaign assets with human approval:

- LinkedIn/company posts.
- Founder posts.
- Email and WhatsApp copy.
- Static creatives.
- Carousels/documents.
- Mini decks and one-pagers.
- Landing-page visuals.
- Template-led 15-45 second short videos.

Assets should be editable where practical and exported in final usable formats.

### Email Integration Layer

Provider-agnostic email layer for:

- Approved email sequence dispatch.
- Reply-to routing.
- Reply sync and classification.
- Event tracking where available.
- Suppression, unsubscribe, bounce, and consent controls.

Supported provider approach:

- First-class mailbox providers: Gmail/Google Workspace, Microsoft 365/Exchange, Zoho Mail.
- Campaign senders: SendGrid, Mailgun, Postmark, Brevo, Amazon SES, or equivalent.
- Fallback: SMTP/IMAP where secure and permitted.

### LinkedIn Review Assistant

Review, recommendation, and tasking only.

The system may summarize approved company-page activity, manually captured founder/key-person post links, or uploaded screenshots. It may recommend a comment, DM angle, connection note, or no action. It must create a human task with the post link/reference and owner.

It must not auto-post, auto-comment, auto-DM, auto-connect, scrape LinkedIn, or capture unauthorized screenshots.

### WhatsApp Layer

Uses compliant WhatsApp Business API paths only. It supports warm/approved conversations, qualification, opt-outs, safe guidance, and human handoff. Personal WhatsApp is not automated or scraped.

### Warm Signal Layer

Unifies events from email, WhatsApp, forms, LinkedIn manual logs, landing pages, downloads, and sales notes into lead scoring and next-best-action recommendations.

### CRM Handoff

Qualified conversations are passed into the client's CRM or sales workflow with source, campaign, lead/contact, context, score, recommended action, and handoff owner.

### AI CMO Review Room

Schedules a weekly or fortnightly voice review with the founder, client sponsor, or growth operator.

Before the review, the system prepares a performance brief covering campaign results, warm signals, qualified conversations, creative performance, stuck items, channel health, usage, and recommended changes.

During the review, the Growth CMO Orchestrator facilitates a structured conversation:

- What happened in the last period.
- What changed in audience, offer, market, or sales feedback.
- Which campaign lanes should scale, pause, revise, or continue.
- Which creative, outreach, LinkedIn, WhatsApp, or handoff processes need adjustment.
- Which action items need owners and due dates.

After the review, the system generates meeting minutes, decision records, an updated action plan, and approval requests. Agreed changes do not automatically alter live campaigns, outbound sequences, pricing, proposals, or public assets until the required human approval gate is completed.

## 6-Week Deployment Flow

1. Week 1: Growth audit, ICP mapping, offer library, sales process review, and channel policy.
2. Week 2: Configure Client Brain, brand kit, proof library, approval rules, integrations, AI CMO review cadence, and CRM handoff.
3. Week 3: Build campaign lanes, prospect criteria, lead scoring, outreach paths, and warm-signal rules.
4. Week 4: Generate campaign kits: copy, creatives, carousels, decks, landing assets, email/WhatsApp/LinkedIn drafts.
5. Week 5: Launch controlled pilot waves with human approvals, LinkedIn tasks, email sends, WhatsApp paths, and signal capture.
6. Week 6: Run the AI CMO review, confirm qualified conversations, creative performance, reply quality, channel health, and next 30-day action plan.

## Differentiation

Clay and Apollo are strong around data, enrichment, and GTM workflows. Outreach and Salesloft are strong around sales engagement execution.

Growth Automation Studio should own a broader operating promise:

Campaign strategy + AI creative production + outreach workflows + warm-signal intelligence + qualified handoff.

Simple line:

> We do not just find prospects. We build the campaign, generate the assets, run the outreach system, and surface qualified conversations.

The AI CMO Review Room adds a recurring executive rhythm: the system does not only report performance; it helps the founder or growth owner decide what to change next and turns those decisions into approved action plans.

## Success Metrics

- Qualified conversations.
- Reply quality.
- Warm signals captured and acted on.
- Campaign asset production speed.
- Approval cycle time.
- Lead handoff completeness.
- Campaign lane scale/pause/revise decision quality.
- AI CMO review completion rate and action-item closure.
- Channel health: email deliverability, WhatsApp handoff quality, LinkedIn task completion.

## Acceptance Scenarios

- A new client receives Client Brain, brand kit, proof library, and 2-3 campaign lanes.
- Agents generate a campaign kit, but risky claims are blocked before approval.
- Gmail, Microsoft 365, or Zoho replies are classified and turned into lead actions.
- LinkedIn Review creates a task with post URL/screenshot, summary, suggested action, and human owner.
- WhatsApp warm replies trigger qualification and handoff.
- Weekly report recommends whether to scale, pause, or revise each campaign lane.
- AI CMO Review captures agreed decisions and creates an approval-gated action plan for the next period.
