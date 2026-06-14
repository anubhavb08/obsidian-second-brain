# Zandem.ai Product Flowcharts

Visual explainer for the Zandem.ai product model, onboarding flow, event loop, and approval boundaries.

## Product In One View

```mermaid
flowchart TB
  B["B2B founder or growth owner"] --> Z["Zandem.ai"]

  Z --> C["Client Brain"]
  Z --> L["Campaign Lanes"]
  Z --> A["AI Creative Studio"]
  Z --> O["Outreach Workflows"]
  Z --> S["Warm Signal Intelligence"]
  Z --> H["CRM / Sales Handoff"]
  Z --> R["AI CMO Review Room"]

  C --> C1["ICP, offers, proof, tone, claims, approvals"]
  L --> L1["Audience, offer, CTA, channel mix, KPI targets"]
  A --> A1["Posts, emails, WhatsApp copy, creatives, decks, videos"]
  O --> O1["Email, LinkedIn tasks, WhatsApp Business paths"]
  S --> S1["Replies, manual logs, forms, downloads, sales notes"]
  H --> H1["Context, score, recommended action, owner"]
  R --> R1["Performance review, decisions, action plan"]

  R1 --> C
  S1 --> H
```

## Operating Model

```mermaid
flowchart TD
  H["Human Growth Owner / Client Sponsor"]
  CMO["Growth CMO Orchestrator"]
  COMP["Compliance & Approval Agent"]
  OPS["Integration & Usage Ops Agent"]

  H --> CMO
  CMO --> CB["Client Brain Agent"]
  CMO --> MR["Market & ICP Research Agent"]
  CMO --> CS["Campaign Strategy Agent"]
  CMO --> PE["Prospecting & Enrichment Agent"]
  CMO --> CT["Content Strategy Agent"]
  CMO --> AC["AI Creative Production Agent"]
  CMO --> EO["Email Outreach Agent"]
  CMO --> LI["LinkedIn Review Agent"]
  CMO --> WA["WhatsApp Assistant Agent"]
  CMO --> RI["Reply Intelligence & Lead Scoring Agent"]
  CMO --> AR["Analytics & Reporting Agent"]
  CMO --> OPS

  COMP -. "veto / block risky actions" .-> EO
  COMP -. "veto / block risky actions" .-> LI
  COMP -. "veto / block risky actions" .-> WA
  COMP -. "veto / block risky actions" .-> AC
  OPS -. "readiness / cost gate" .-> CMO
```

## AI-Led Onboarding Setup

```mermaid
flowchart LR
  A["Account setup"] --> B["Upload context"]
  B --> C["Choose CMO style"]
  C --> D["First CMO conversation"]
  D --> E["Auto-generate setup"]
  E --> F["Human confirmation"]
  F --> G["Activate first campaign system"]

  B --> B1["Website, deck, case studies, proof, CRM notes"]
  C --> C1["Strategic, operator, creative, conservative, founder coach"]
  D --> D1["ICP, offer, differentiation, channels, constraints, goals"]
  E --> E1["Client Brain, campaign lanes, assets, rules, handoff, review cadence"]
  F --> F1["Approve, edit, or flag assumptions"]

  F1 -->|Approved| G
  F1 -->|Needs edits| D
```

CMO style changes the facilitation tone and working rhythm. It does not override compliance, approval rules, claim boundaries, or channel guardrails.

## End-To-End Event Loop

```mermaid
flowchart LR
  A["Client onboarding"] --> B["Client Brain"]
  B --> C["Campaign Strategy"]
  C --> D["Campaign lanes"]
  D --> E["Prospecting + enrichment"]
  D --> F["AI content + creative production"]
  F --> G["Quality + compliance review"]
  E --> G
  G --> H["Human approval queue"]
  H --> I["Email / WhatsApp / LinkedIn tasking"]
  I --> J["Channel events + manual logs"]
  J --> K["Reply intelligence + warm signals"]
  K --> L["Lead scoring + next-best action"]
  L --> M["CRM / sales handoff"]
  K --> N["Analytics + weekly report"]
  N --> O["AI CMO review"]
  O --> P["Decision record + action plan"]
  P --> C
  P --> H
```

## Review Room Decision Loop

```mermaid
flowchart TB
  A["Analytics prepares review brief"] --> B["AI CMO voice review"]
  B --> C["Discuss performance"]
  B --> D["Discuss market or sales feedback"]
  B --> E["Discuss campaign changes"]

  C --> F["Decision record"]
  D --> F
  E --> F

  F --> G["Action plan"]
  G --> H["Approval requests"]
  H --> I["Approved changes"]
  H --> J["Blocked or revised changes"]

  I --> K["Next campaign cycle"]
  J --> B
```

## Approval Boundary

```mermaid
flowchart LR
  A["Agent recommendation"] --> B["Draft / task / decision record"]
  B --> C{"Sensitive action?"}
  C -->|No| D["Can enter operating queue"]
  C -->|Yes| E["Compliance review"]
  E --> F["Human approval"]
  F -->|Approved| G["Execution allowed"]
  F -->|Rejected| H["Revise or block"]

  E -. "veto" .-> H
```

Sensitive actions include public content, outbound sends, LinkedIn actions, WhatsApp templates, campaign activation, pricing, proposals, client references, CRM handoff rule changes, and major strategy changes.
