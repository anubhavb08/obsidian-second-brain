# Tooling Stack

## Decision

Add tooling now as an architecture layer, not as final vendor procurement.

The product should define which tool capabilities every deployment needs, which vendors are candidate adapters, and which decisions can safely wait until pilot design, pricing, compliance, and client context are clearer.

This prevents the architecture from becoming vague while keeping us free to swap providers later.

## Tooling Principles

- Tools are adapters under Growth Automation Studio, not the product itself.
- Every tool must map to an agent, event type, data object, and approval boundary.
- Client data, consent, suppression, and audit logs stay in the Growth Automation Studio system of record.
- Vendor choice should be made per capability, not by buying one giant stack too early.
- The first version should prefer fewer, reliable adapters over a sprawling marketplace of integrations.

## Tool Layers

### 1. Agent Runtime And Orchestration

Purpose: run the 14 logical agents, tool calls, handoffs, traces, guardrails, and scheduled jobs.

Required capabilities:

- Agent definitions with instructions, model, tools, and structured output schema.
- Orchestrator-to-specialist handoff.
- Code-driven workflow control for repeatable campaign flows.
- Trace logs, run history, retries, and failure states.
- Human approval gates before public or channel actions.
- Scheduled voice review sessions for AI CMO performance reviews and decision capture.
- Meeting transcripts, summaries, decision records, and action-plan generation.

Candidate direction:

- Use an agent SDK or custom orchestrator with explicit state and event logs.
- OpenAI Agents SDK is a strong candidate for model-backed agents because its docs describe agents as configured with instructions, a model, and tools, and support orchestration/handoffs.
- A realtime voice layer is a candidate for the AI CMO Review Room, with the voice session treated as an input channel into the same approval-gated event system.

### 2. Agent Brain And Knowledge Layer

Purpose: give every agent client-specific memory and context.

Required capabilities:

- Client Brain store: ICP, offers, tone, brand kit, proof rules, claim boundaries, approvals, CRM handoff.
- Prompt registry with versions, QA status, and safety rules.
- Retrieval over client documents, website copy, case studies, CRM exports, decks, and proof assets.
- Structured output schemas per agent.
- Evaluation records for quality, safety, usefulness, and approval safety.

Candidate direction:

- LLM provider layer for reasoning and generation.
- Relational database for client system of record.
- Vector/retrieval layer for client docs and proof assets.
- Object storage for creative exports and uploaded evidence.

### 3. Prospect Discovery And Contact Credential Layer

Purpose: find, enrich, deduplicate, and qualify prospects for campaign lanes.

Required capabilities:

- Company/account search.
- People search by role, seniority, geography, industry, company size, and campaign criteria.
- Email and phone enrichment where permitted.
- Waterfall enrichment across multiple sources where useful.
- Deduplication, source confidence, credit tracking, and suppression checks.
- Consent and legitimate-interest review before outreach.

Candidate direction:

- Apollo as a first candidate for people search and enrichment. Apollo’s API docs describe people search, enrichment endpoints, and optional email/phone reveal parameters.
- Clay as a candidate GTM research/enrichment workbench, especially for custom account research and workflow orchestration. Clay describes Claygent as an AI agent for GTM research, orchestration, and content/workflow execution.
- Keep a provider abstraction so ZoomInfo, Lusha, Clearbit-style sources, or India-specific databases can be evaluated later without changing the core product.

### 4. Outreach Channel Layer

Purpose: execute approved outreach and ingest channel signals.

Email:

- Provider-agnostic adapters for Gmail/Google Workspace, Microsoft 365/Exchange, Zoho Mail, campaign senders, and SMTP/IMAP fallback.
- Support send requests, reply sync, event tracking where available, unsubscribe, bounce, and suppression handling.

LinkedIn:

- Review, recommendation, and tasking only.
- Official API where available for authorized company pages.
- Manual link/screenshot capture for founder/key-person pages.
- No scraping, auto-posting, auto-commenting, auto-DM, or auto-connect.

WhatsApp:

- WhatsApp Business API provider layer only.
- Personal WhatsApp is out of scope.
- Human handoff for pricing, proposals, meetings, complex briefs, low confidence, and high-value leads.

### 5. AI Creative Production Layer

Purpose: generate campaign kits without depending on routine manual designers or video editors.

Required capabilities:

- Copy generation.
- Static image generation or composition.
- Carousel/document generation.
- Mini deck and one-pager generation.
- Landing-page visual generation.
- Template-led 15-45 second short video generation.
- Editable source plus export when practical.
- Strict brand-kit enforcement and human approval.

Candidate direction:

- Use a modular creative-provider layer rather than committing to one tool now.
- Candidate providers can be evaluated by output quality, editability, cost, API support, brand control, and commercial licensing.

### 6. CRM And Sales Handoff Layer

Purpose: pass qualified conversations into the client’s CRM or sales workflow.

Required capabilities:

- Create/update contact, company, lead, deal/opportunity, task, and note records.
- Preserve source campaign, conversation context, score, next-best action, and owner.
- Support HubSpot, Zoho CRM, Salesforce, Bigin, Pipedrive, or CSV/manual handoff depending on client stack.

Candidate direction:

- Start with one or two CRM adapters plus a clean export/manual fallback.
- HubSpot is a likely first adapter because its CRM contacts API supports contact read/write and sync use cases.

### 7. Usage, Billing, And Operations Layer

Purpose: make retainers and credits measurable later.

Required capabilities:

- Track AI tokens/runs.
- Track enrichment credits.
- Track email sends, mailbox sync, and campaign sender costs.
- Track WhatsApp conversations/templates.
- Track creative generation costs.
- Track storage and export usage.
- Show client-level usage and internal margin visibility.

Commercials can be decided later, but usage metering must be designed from the beginning.

## What To Decide Now

- Tool categories and adapter boundaries.
- Minimum required tools for pilot delivery.
- Data model for usage metering and audit logs.
- Which agent can call which tool.
- Which actions require human approval.

## What To Decide Later

- Final vendor stack per category.
- Bundle size and included monthly credits.
- Whether to offer client-owned accounts, Studio-owned accounts, or hybrid accounts.
- Volume limits per plan.
- Procurement, compliance review, and data processing agreements.
- Whether Clay/Apollo or other enrichment providers become default or optional.

## Reference Sources

- OpenAI Agents SDK: https://platform.openai.com/docs/guides/agents-sdk/
- OpenAI Agents SDK orchestration: https://openai.github.io/openai-agents-python/multi_agent/
- Apollo API overview: https://docs.apollo.io/docs/api-overview
- Apollo People Enrichment: https://docs.apollo.io/reference/people-enrichment
- Claygent: https://www.clay.com/claygent
- HubSpot CRM Contacts API: https://developers.hubspot.com/docs/api-reference/latest/crm/objects/contacts/guide
