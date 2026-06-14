# Zlicc Growth Console Low-Fidelity Wireframes

Version: 0.2  
Created: 2026-05-21  
Updated: 2026-05-22  
Purpose: Consolidated low-fidelity screen blueprint for review before detailed UI design and Sprint 0.

---

## 1. Wireframe Principles

The Growth Console should feel like a daily operating console for growth, not a traditional CRM.

Each screen should answer one practical question:

- What needs attention?
- What should be approved?
- Who should be pursued?
- What should be created?
- What should be sent?
- What has changed?
- What should the team do next?

Global UX rules:

- Keep the CMO Brain visible as decision support, not as a chatbot.
- Keep every AI recommendation explainable.
- Keep LinkedIn human-in-loop.
- Keep personal WhatsApp manual through Quick Capture.
- Keep campaign focus limited to three active lanes.
- Keep approvals close to the action.
- Keep operational queues simple and fast.
- Start every user on Today, but customize Today by role, assigned work, and relevant trackers.
- Give Approvals a dedicated module while also showing contextual approval prompts inside each workflow.
- Treat existing customers as warm audience segments for communication, education, cross-sell, and upsell, not as a separate full CRM workflow in V1.
- Show integration spend and usage in Admin / Integrations through a clear dashboard, not on the general Today screen.
- Preserve learning feedback from approvals, edits, replies, performance, and overrides so the CMO Brain and specialist agents improve over time.

Role-specific Today rule:

- Founder / Marketing Owner: campaign lanes, hot replies, approvals, handoffs, blockers, CMO recommendations.
- LinkedIn Operator: assigned LinkedIn queue, due tasks, suggested copy, response logging, limited prospect context.
- Creative Team Member: assigned production tasks, deadlines, review comments, upload actions, revision requests.
- Sales / Handoff Owner: hot replies, WhatsApp handoffs, meeting/proposal requests, follow-up tasks.
- Admin: system health, integration failures, API usage alerts, user/access issues.

---

## 2. Global App Shell

All screens use a consistent shell:

```text
+------------------------------------------------------------------------------+
| Zlicc Growth Console                                      Search      Profile |
+------------------+-----------------------------------------------------------+
| NAVIGATION       | SCREEN TITLE                                              |
|                  | Screen-specific summary, filters, actions                  |
| Command          |                                                           |
| - Today          | Main content area                                          |
| - Approvals      |                                                           |
| - Tasks          |                                                           |
|                  |                                                           |
| Prospecting      |                                                           |
| - Leads          |                                                           |
| - Quick Capture  |                                                           |
| - Apollo         |                                                           |
| - LinkedIn       |                                                           |
| - Customers      |                                                           |
|                  |                                                           |
| Campaigns        |                                                           |
| - Portfolio      |                                                           |
| - Calendar       |                                                           |
| - Landing Pages  |                                                           |
|                  |                                                           |
| Content          |                                                           |
| - Studio         |                                                           |
| - LinkedIn Posts |                                                           |
| - Newsletters    |                                                           |
| - Creative Desk  |                                                           |
| - Assets         |                                                           |
|                  |                                                           |
| Outreach         |                                                           |
| - Email          |                                                           |
| - WhatsApp       |                                                           |
| - Replies        |                                                           |
|                  |                                                           |
| Intelligence     |                                                           |
| - CMO Brain      |                                                           |
| - Agent Ops      |                                                           |
| - Analytics      |                                                           |
|                  |                                                           |
| Admin            |                                                           |
+------------------+-----------------------------------------------------------+
```

---

## 3. Today / Command Centre

Question answered:

What should Zlicc do today to create more qualified conversations?

```text
+------------------------------------------------------------------------------+
| Zlicc Growth Console                                      Search      Profile |
+------------------+-----------------------------------------------------------+
| NAVIGATION       | TODAY / COMMAND CENTRE                                    |
| > Today          | Thursday, 21 May 2026                                     |
|                  |                                                           |
|                  | +-------------------------------------------------------+ |
|                  | | CMO BRAIN PRIORITY                                    | |
|                  | |                                                       | |
|                  | | Push AGM lane this week. 14 warm prospects need       | |
|                  | | follow-up. Exhibition lane is blocked by proof asset. | |
|                  | |                                                       | |
|                  | | [Review Recommendation] [Open Weekly Plan]            | |
|                  | +-------------------------------------------------------+ |
|                  |                                                           |
|                  | +-------------+ +-------------+ +-------------+ +-------+ |
|                  | | Hot Replies | | Approvals   | | WA Handoffs | | Tasks | |
|                  | | 7           | | 12          | | 3           | | 18    | |
|                  | | +3 urgent   | | 5 content   | | 2 pricing   | | 6 OD  | |
|                  | | [Open]      | | [Review]    | | [Assign]    | |[Open] | |
|                  | +-------------+ +-------------+ +-------------+ +-------+ |
|                  |                                                           |
|                  | +-------------------------------------------------------+ |
|                  | | ACTIVE CAMPAIGN LANES                         3 / 3  | |
|                  | +-------------------------------------------------------+ |
|                  | | Campaign              Status    Today        Health   | |
|                  | | AGM Outreach          Active    8 followups  Good     | |
|                  | | Exhibition Stack      Active    asset due    Blocked  | |
|                  | | Agency Tech Partner   Active    21 LI tasks  Watch    | |
|                  | |                                                       | |
|                  | | [Open Portfolio] [Resolve Blockers]                  | |
|                  | +-------------------------------------------------------+ |
|                  |                                                           |
|                  | +------------------------------+ +----------------------+ |
|                  | | HOT LEADS                    | | WORK QUEUES          | |
|                  | |                              | |                      | |
|                  | | 1. Priya S.                  | | LinkedIn tasks   42  | |
|                  | |    Meeting intent            | | Creative pending 9   | |
|                  | |    [Open] [Assign]           | | Landing review   2   | |
|                  | |                              | | Content review   11  | |
|                  | | 2. Agency founder            | | Email sequences  3   | |
|                  | |    Asked for deck            | |                      | |
|                  | |    [Send Details]            | | [Open Queue]         | |
|                  | +------------------------------+ +----------------------+ |
|                  |                                                           |
|                  | +-------------------------------------------------------+ |
|                  | | WEEKLY LEARNING                                      | |
|                  | | Working: AGM secure webcast angle                    | |
|                  | | Weak: Exhibition campaign lacks proof assets         | |
|                  | | Next: Add proof-led carousel and landing page CTA    | |
|                  | | [Open Analytics] [Generate Friday Report]            | |
|                  | +-------------------------------------------------------+ |
+------------------+-----------------------------------------------------------+
```

Primary actions:

- Review CMO recommendation.
- Open hot lead.
- Review approvals.
- Assign handoff.
- Resolve blockers.
- Generate weekly report.

Role behavior:

- Today is the default landing screen for all users.
- The screen content changes by role and assignment; it should not show every dashboard to every user.
- Users should see the work they can act on today, plus just enough context to understand why it matters.

---

## 4. Approvals

Question answered:

What needs human approval before it can go live or be sent?

```text
+------------------------------------------------------------------------------+
| Zlicc Growth Console                                      Search      Profile |
+------------------+-----------------------------------------------------------+
| NAVIGATION       | APPROVALS                                                 |
| > Approvals      | Pending: 22    High risk: 4    Due today: 9               |
|                  |                                                           |
|                  | +-------------------------------------------------------+ |
|                  | | FILTERS                                               | |
|                  | | [All] [Content] [Landing Pages] [Email] [WhatsApp]    | |
|                  | | [Campaigns] [Client Proof] [Claims] [High Risk]       | |
|                  | +-------------------------------------------------------+ |
|                  |                                                           |
|                  | +------------------------------+ +----------------------+ |
|                  | | APPROVAL QUEUE               | | SELECTED ITEM        | |
|                  | |                              | |                      | |
|                  | | > AGM landing page           | | AGM landing page     | |
|                  | |   High priority              | | Campaign: AGM lane   | |
|                  | |   Needs publish approval     | | Risk: Medium         | |
|                  | |                              | | Quality: 8.4         | |
|                  | |   WhatsApp template          | |                      | |
|                  | |   Needs compliance approval  | | CMO reason:          | |
|                  | |                              | | Page is strong, but  | |
|                  | |   Exhibition carousel        | | claims around secure | |
|                  | |   Needs proof check          | | access need review.  | |
|                  | |                              | |                      | |
|                  | |   Email sequence             | | [Preview]            | |
|                  | |   Ready for approval         | | [Open Source]        | |
|                  | |                              | |                      | |
|                  | +------------------------------+ +----------------------+ |
|                  |                                                           |
|                  | +-------------------------------------------------------+ |
|                  | | REVIEW ACTIONS                                        | |
|                  | | [Approve] [Edit] [Request Revision] [Reject]          | |
|                  | | Comment                                               | |
|                  | | [ Add review note...                                ] | |
|                  | +-------------------------------------------------------+ |
+------------------+-----------------------------------------------------------+
```

Primary actions:

- Approve.
- Edit.
- Request revision.
- Reject.
- Preview.
- Open source record.

---

## 5. Tasks

Question answered:

What work is due, overdue, assigned, or blocked?

```text
+------------------------------------------------------------------------------+
| Zlicc Growth Console                                      Search      Profile |
+------------------+-----------------------------------------------------------+
| NAVIGATION       | TASKS                                                     |
| > Tasks          | My tasks: 18    Overdue: 6    Team tasks: 74              |
|                  |                                                           |
|                  | +-------------------------------------------------------+ |
|                  | | FILTERS                                               | |
|                  | | [Mine] [Team] [Overdue] [Today] [This Week]           | |
|                  | | Owner [All v]  Type [All v]  Campaign [All v]         | |
|                  | +-------------------------------------------------------+ |
|                  |                                                           |
|                  | +-------------------------------------------------------+ |
|                  | | TASK LIST                                             | |
|                  | +-------------------------------------------------------+ |
|                  | | Due        Priority  Task             Owner   Status   | |
|                  | | Today      High      Call Priya S.    Sales   Open     | |
|                  | | Today      High      Approve AGM LP   Founder Open     | |
|                  | | Overdue    High      Exhibition proof Creative Blocked | |
|                  | | Tomorrow   Medium    LinkedIn batch   Ankit   Open     | |
|                  | | Friday     Medium    Newsletter draft Content Draft    | |
|                  | +-------------------------------------------------------+ |
|                  |                                                           |
|                  | +------------------------------+ +----------------------+ |
|                  | | SELECTED TASK                | | RELATED CONTEXT      | |
|                  | |                              | | Lead: Priya S.       | |
|                  | | Call Priya S.                | | Campaign: AGM        | |
|                  | | Reason: Meeting intent       | | Score: 84            | |
|                  | | Due: Today                   | | Last signal: Reply   | |
|                  | |                              | |                      | |
|                  | | [Done] [Snooze] [Reassign]   | | [Open Lead]          | |
|                  | | [Cancel]                     | | [Open Campaign]      | |
|                  | +------------------------------+ +----------------------+ |
+------------------+-----------------------------------------------------------+
```

Primary actions:

- Complete task.
- Snooze.
- Reassign.
- Open related lead/campaign.
- Create task.

---

## 6. Lead List

Question answered:

Which leads should be worked right now?

```text
+------------------------------------------------------------------------------+
| Zlicc Growth Console                                      Search      Profile |
+------------------+-----------------------------------------------------------+
| NAVIGATION       | LEADS                                                     |
| > Leads          | Total: 1,248    Hot: 42    New this week: 180             |
|                  |                                                           |
|                  | +-------------------------------------------------------+ |
|                  | | FILTERS                                               | |
|                  | | Stage [All v] Score [70+ v] Campaign [All v]          | |
|                  | | Source [All v] Owner [All v] Next Action [All v]      | |
|                  | | [Import] [Add Lead] [Enrich Selected]                 | |
|                  | +-------------------------------------------------------+ |
|                  |                                                           |
|                  | +-------------------------------------------------------+ |
|                  | | LEAD TABLE                                            | |
|                  | +-------------------------------------------------------+ |
|                  | | Score Lead / Company       Stage      Campaign Action  | |
|                  | | 84    Priya S. / Listed Co Replied    AGM      Call    | |
|                  | | 78    Rahul M. / Finverse  Warmed     Pulse    WA      | |
|                  | | 71    Nisha R. / Agency    Connected  Agency   LI DM   | |
|                  | | 66    Amit K. / BFSI       Enriched   GFF      Email   | |
|                  | +-------------------------------------------------------+ |
|                  |                                                           |
|                  | +------------------------------+ +----------------------+ |
|                  | | CMO INSIGHT                  | | BULK ACTIONS         | |
|                  | | 18 AGM leads crossed hot     | | [Assign Owner]       | |
|                  | | threshold after deck clicks. | | [Add to Campaign]    | |
|                  | | Prioritize follow-up today.  | | [Create LI Tasks]    | |
|                  | |                              | | [Export]             | |
|                  | +------------------------------+ +----------------------+ |
+------------------+-----------------------------------------------------------+
```

Primary actions:

- Filter leads.
- Open lead.
- Enrich selected.
- Add to campaign.
- Create tasks.
- Assign owner.

---

## 7. Lead Detail

Question answered:

Who is this prospect, why are they important, and what should we do next?

```text
+------------------------------------------------------------------------------+
| Zlicc Growth Console                                      Search      Profile |
+------------------+-----------------------------------------------------------+
| NAVIGATION       | LEAD DETAIL                                               |
| > Leads          | Priya Sharma                                              |
|                  | Company Secretary, Listed Manufacturing Co.               |
|                  | Source: Apollo + LinkedIn    Campaign: AGM Outreach       |
|                  |                                                           |
|                  | +-------------------------------------------------------+ |
|                  | | LEAD INTELLIGENCE                                    | |
|                  | | Score: 84 / 100          Stage: Replied / Hot         | |
|                  | | Offer Fit: Hybrid AGM + Secure Webcast + AI Summary   | |
|                  | | Pillars: ZliccLive, ZliccSync, ZliccAI, ZliccStudio   | |
|                  | |                                                       | |
|                  | | Why this lead matters:                               | |
|                  | | - Relevant AGM planning window                        | |
|                  | | - Role owns compliance and meeting execution           | |
|                  | | - Opened deck twice and replied asking for details     | |
|                  | +-------------------------------------------------------+ |
|                  |                                                           |
|                  | +-------------------------------------------------------+ |
|                  | | NEXT BEST ACTION                                     | |
|                  | | Send AGM capability deck and ask for 15-minute call.  | |
|                  | | Keep message compliance-led, not flashy.              | |
|                  | |                                                       | |
|                  | | [Send Details] [Assign Follow-up] [Book Meeting]      | |
|                  | | [Move to Nurture] [Mark Not Relevant]                 | |
|                  | +-------------------------------------------------------+ |
|                  |                                                           |
|                  | +------------------------------+ +----------------------+ |
|                  | | CONTACT / ACCOUNT            | | WARM SIGNALS         | |
|                  | | Email: priya@company.com     | | Email opened    +5   | |
|                  | | Phone: +91 XXXXX XXXXX       | | Deck clicked    +12  | |
|                  | | LinkedIn: Open profile       | | Outlook reply   +25  | |
|                  | | City: Mumbai                 | | LinkedIn log    +8   | |
|                  | | Industry: Manufacturing      | | Landing visit   +10  | |
|                  | | Company type: Listed Co.     | | [View All]           | |
|                  | +------------------------------+ +----------------------+ |
|                  |                                                           |
|                  | +-------------------------------------------------------+ |
|                  | | TIMELINE                                             | |
|                  | | Today 11:22   Outlook reply received                 | |
|                  | | Today 09:14   Deck clicked                           | |
|                  | | Yesterday     LinkedIn connection accepted            | |
|                  | | 2 days ago    AGM campaign email sent                 | |
|                  | | 3 days ago    Apollo enrichment completed             | |
|                  | | [Add Note] [Log Call] [Upload File]                   | |
|                  | +-------------------------------------------------------+ |
+------------------+-----------------------------------------------------------+
```

Primary actions:

- Send details.
- Assign follow-up.
- Book meeting.
- Add note.
- Log call.
- Move to nurture.

---

## 8. Quick Capture

Question answered:

How do I capture a real-world brief or conversation in under one minute?

```text
+------------------------------------------------------------------------------+
| Zlicc Growth Console                                      Search      Profile |
+------------------+-----------------------------------------------------------+
| NAVIGATION       | QUICK CAPTURE                                             |
| > Quick Capture  | Capture personal WhatsApp briefs, calls, referrals        |
|                  |                                                           |
|                  | +-------------------------------------------------------+ |
|                  | | FAST ENTRY                                           | |
|                  | | Source                                                | |
|                  | | [Personal WhatsApp v]                                | |
|                  | |                                                       | |
|                  | | Contact Name              Company Name                | |
|                  | | [Rahul Mehta          ]   [Finverse Events       ]    | |
|                  | |                                                       | |
|                  | | Mobile / WhatsApp        Email                        | |
|                  | | [+91 XXXXX XXXXX     ]   [rahul@finverse.com     ]    | |
|                  | |                                                       | |
|                  | | LinkedIn URL                                          | |
|                  | | [linkedin.com/in/...                              ]    | |
|                  | |                                                       | |
|                  | | Brief Notes                                           | |
|                  | | [Looking for interactive engagement ideas for BFSI ]   | |
|                  | | [leadership event in July. Asked for QR games.     ]   | |
|                  | |                                                       | |
|                  | | Required Solution / Event Type                         | |
|                  | | [Audience Engagement / Leadership Event v]            | |
|                  | |                                                       | |
|                  | | Next Follow-up Date                                   | |
|                  | | [24 May 2026]                                         | |
|                  | |                                                       | |
|                  | | Attach Files / Links                                  | |
|                  | | [Upload PPT/PDF/Image/Video] [Add Link]               | |
|                  | |                                                       | |
|                  | | [Save Lead] [Save + Ask CMO Brain] [Cancel]           | |
|                  | +-------------------------------------------------------+ |
|                  |                                                           |
|                  | +------------------------------+ +----------------------+ |
|                  | | POSSIBLE MATCHES             | | CMO PREVIEW          | |
|                  | | No exact match found          | | After saving:        | |
|                  | | Similar: Finverse Tech        | | - Audience           | |
|                  | | [Use Existing] [Create New]   | | - Offer fit          | |
|                  | |                              | | - Pillars            | |
|                  | |                              | | - Lead score         | |
|                  | |                              | | - Next action        | |
|                  | +------------------------------+ +----------------------+ |
+------------------+-----------------------------------------------------------+
```

Primary actions:

- Save lead.
- Save and ask CMO Brain.
- Upload file.
- Use existing match.
- Create new contact/company.

---

## 9. Apollo Prospecting

Question answered:

How do we build and enrich targeted prospect lists for campaigns?

```text
+------------------------------------------------------------------------------+
| Zlicc Growth Console                                      Search      Profile |
+------------------+-----------------------------------------------------------+
| NAVIGATION       | APOLLO PROSPECTING                                        |
| > Apollo         | Build targeted lists and enrich leads                     |
|                  |                                                           |
|                  | +-------------------------------------------------------+ |
|                  | | SEARCH CRITERIA                                      | |
|                  | | Campaign [AGM Outreach v]                             | |
|                  | | Industry [BFSI, Listed Companies, Manufacturing]      | |
|                  | | Roles [Company Secretary, Investor Relations]          | |
|                  | | Location [India v]   Seniority [Director+ v]          | |
|                  | | Company Size [500+ v]                                 | |
|                  | | [Search Apollo] [Save Criteria]                       | |
|                  | +-------------------------------------------------------+ |
|                  |                                                           |
|                  | +-------------------------------------------------------+ |
|                  | | RESULTS PREVIEW                                      | |
|                  | +-------------------------------------------------------+ |
|                  | | Name          Company           Role      Confidence   | |
|                  | | Priya S.      Listed Co.        CS        High         | |
|                  | | Amit K.       BFSI Group        IR Head   Medium       | |
|                  | | Neeraj P.     Manufacturing     CS        High         | |
|                  | +-------------------------------------------------------+ |
|                  | | [Import Selected] [Import All] [Exclude Duplicates]    | |
|                  | +-------------------------------------------------------+ |
|                  |                                                           |
|                  | +------------------------------+ +----------------------+ |
|                  | | IMPORT SUMMARY               | | ENRICHMENT QUEUE     | |
|                  | | New: 82                       | | Pending: 41          | |
|                  | | Existing updated: 18          | | Failed: 3            | |
|                  | | Duplicates skipped: 9         | | Credits used: 120    | |
|                  | | [View Import Job]             | | [Retry Failed]       | |
|                  | +------------------------------+ +----------------------+ |
+------------------+-----------------------------------------------------------+
```

Primary actions:

- Search Apollo.
- Import selected.
- Enrich leads.
- View import job.
- Retry failed enrichment.

---

## 10. LinkedIn Workbench

Question answered:

Which LinkedIn actions should be done today, what should I say, and how do I log the result?

```text
+------------------------------------------------------------------------------+
| Zlicc Growth Console                                      Search      Profile |
+------------------+-----------------------------------------------------------+
| NAVIGATION       | LINKEDIN WORKBENCH                                        |
| > LinkedIn       | Assigned to: Ankit                                        |
|                  |                                                           |
|                  | +-------------------------------------------------------+ |
|                  | | TODAY'S LINKEDIN QUEUE                               | |
|                  | | Today: 24    Overdue: 9    High Priority: 6           | |
|                  | | [Today] [Overdue] [High Priority] [Replied] [Snoozed] | |
|                  | +-------------------------------------------------------+ |
|                  |                                                           |
|                  | +------------------------------+ +----------------------+ |
|                  | | TASK LIST                    | | TASK DETAIL          | |
|                  | | > Priya Sharma               | | Priya Sharma         | |
|                  | |   Comment on post            | | Company Secretary    | |
|                  | |   Score: 84                  | | Campaign: AGM        | |
|                  | |                              | | Offer: Secure AGM    | |
|                  | |   Rahul Mehta                | | Pillars: Live, Sync  | |
|                  | |   Send connection            | |                      | |
|                  | |   Score: 71                  | | Why this action:     | |
|                  | |                              | | Posted about AGM     | |
|                  | |   Nisha Rao                  | | governance last week.| |
|                  | |   Follow-up DM               | |                      | |
|                  | |   Score: 68                  | | [Open LinkedIn]      | |
|                  | |                              | | [Open Lead Detail]   | |
|                  | +------------------------------+ +----------------------+ |
|                  |                                                           |
|                  | +-------------------------------------------------------+ |
|                  | | SUGGESTED COPY                                       | |
|                  | | Type: Comment                                         | |
|                  | | "This is exactly where planning quality matters..."   | |
|                  | | [Copy] [Regenerate] [Request Review]                 | |
|                  | +-------------------------------------------------------+ |
|                  |                                                           |
|                  | +-------------------------------------------------------+ |
|                  | | LOG OUTCOME                                          | |
|                  | | [Done] [Skipped] [No Relevant Post] [Connection Sent] | |
|                  | | [Connected] [DM Sent] [Replied] [Not Relevant]        | |
|                  | | Note [Added thoughtful comment on AGM post...]        | |
|                  | | [Save Outcome]                                       | |
|                  | +-------------------------------------------------------+ |
+------------------+-----------------------------------------------------------+
```

Primary actions:

- Open LinkedIn manually.
- Copy suggested copy.
- Log outcome.
- Mark replied.
- Snooze.

Visibility rule:

- LinkedIn Operators should see only assigned task context, not full campaign performance.
- They may see the campaign name, offer, pillar stack, lead score, and "why this action" explanation because that helps them act intelligently.
- They should not see strategic campaign analytics, conversion performance, budget, CMO portfolio decisions, or broader prospecting strategy.

---

## 11. Existing Customers

Question answered:

Which known customers or contacts should be educated, expanded, or reactivated?

```text
+------------------------------------------------------------------------------+
| Zlicc Growth Console                                      Search      Profile |
+------------------+-----------------------------------------------------------+
| NAVIGATION       | EXISTING CUSTOMERS                                        |
| > Customers      | Known contacts: 426    Expansion candidates: 58           |
|                  |                                                           |
|                  | +-------------------------------------------------------+ |
|                  | | SEGMENTS                                              | |
|                  | | [Past Event Clients] [Agencies] [BFSI] [Warm Leads]   | |
|                  | | [Dormant] [Cross-sell Ready] [Needs Permission]       | |
|                  | +-------------------------------------------------------+ |
|                  |                                                           |
|                  | +-------------------------------------------------------+ |
|                  | | CUSTOMER EXPANSION LIST                               | |
|                  | +-------------------------------------------------------+ |
|                  | | Company         Past Work     Suggested Offer  Status  | |
|                  | | HDFC            Engagement    AI Moments       Warm    | |
|                  | | Brand Agency    Activation    Pulse + XR       Active  | |
|                  | | Pharma Co.      Conference    Live + AI        Dormant | |
|                  | +-------------------------------------------------------+ |
|                  |                                                           |
|                  | +------------------------------+ +----------------------+ |
|                  | | CMO RECOMMENDATION           | | ACTIONS              | |
|                  | | Run education campaign for    | | [Create Segment]     | |
|                  | | past event clients around AI  | | [Add to Campaign]    | |
|                  | | summaries and event content.  | | [Import CSV]         | |
|                  | +------------------------------+ +----------------------+ |
+------------------+-----------------------------------------------------------+
```

Primary actions:

- Import customers.
- Create segment.
- Add to campaign.
- Review expansion recommendation.

V1 positioning:

- Existing customers stay in the audience/prospecting area in V1.
- They are included so the same campaign intelligence can decide which known customers should receive education, cross-sell, upsell, or reactivation communication.
- This is not a replacement for Bigin customer lifecycle management.
- A separate top-level Expansion module can be considered later if customer expansion becomes a large independent workflow.

---

## 12. Campaign Portfolio

Question answered:

Which campaigns are active, which are blocked, and where should we focus this week?

```text
+------------------------------------------------------------------------------+
| Zlicc Growth Console                                      Search      Profile |
+------------------+-----------------------------------------------------------+
| NAVIGATION       | CAMPAIGN PORTFOLIO                                        |
| > Portfolio      | Week: 21 May 2026                                         |
|                  |                                                           |
|                  | +-------------------------------------------------------+ |
|                  | | PORTFOLIO STATUS                            3 / 3 Live | |
|                  | | AGM lane is strongest. Exhibition lane needs proof.   | |
|                  | | Agency lane is LinkedIn-heavy nurture this week.      | |
|                  | | [Review CMO Recommendation] [Create New Campaign]     | |
|                  | +-------------------------------------------------------+ |
|                  |                                                           |
|                  | +-------------------------------------------------------+ |
|                  | | ACTIVE CAMPAIGN LANES                                | |
|                  | +-------------------------------------------------------+ |
|                  | | 1. AGM / Investor Communication                       | |
|                  | | Status: Active    Tier: Aggressive Prospecting        | |
|                  | | Audience: Company Secretaries, IR, Listed Companies   | |
|                  | | Offer: Secure AGM + Webcast + AI Summary              | |
|                  | | LP: Published   Content: Ready                        | |
|                  | | Leads:184 Hot:14 Replies:7 Meetings:2 Health: Good    | |
|                  | | [Open] [Add Leads] [View Content] [Pause]             | |
|                  | +-------------------------------------------------------+ |
|                  | | 2. Exhibition / Booth Intelligence                    | |
|                  | | LP: Draft   Content: Needs Proof   Health: Blocked    | |
|                  | | [Open] [Assign Creative] [Review Page] [Pause]        | |
|                  | +-------------------------------------------------------+ |
|                  | | 3. Agency Tech Partner Push                           | |
|                  | | LP: Published   Content: Scheduled   Health: Watch    | |
|                  | | [Open] [Open LinkedIn Tasks] [View Content] [Pause]   | |
|                  | +-------------------------------------------------------+ |
|                  |                                                           |
|                  | +------------------------------+ +----------------------+ |
|                  | | DRAFT / SCHEDULED            | | BLOCKERS             | |
|                  | | Product Launch Experience    | | Exhibition proof     | |
|                  | | Festive Activation Pulse     | | 9 LinkedIn tasks OD  | |
|                  | | Customer Expansion           | | 2 landing reviews    | |
|                  | | [View All Drafts]            | | [Resolve Blockers]   | |
|                  | +------------------------------+ +----------------------+ |
+------------------+-----------------------------------------------------------+
```

Primary actions:

- Create campaign.
- Activate/pause.
- Add leads.
- Assign creative.
- Review landing page.

---

## 13. Seasonal Calendar

Question answered:

What upcoming timing windows should trigger campaigns?

```text
+------------------------------------------------------------------------------+
| Zlicc Growth Console                                      Search      Profile |
+------------------+-----------------------------------------------------------+
| NAVIGATION       | SEASONAL CALENDAR                                         |
| > Calendar       | View: Quarter    Manual entries: 18    AI suggestions: 7  |
|                  |                                                           |
|                  | +-------------------------------------------------------+ |
|                  | | CALENDAR CONTROLS                                    | |
|                  | | [Month] [Quarter] [List]                             | |
|                  | | Category [All v] Priority [All v] Source [All v]      | |
|                  | | [Add Manual Opportunity] [Ask Market Research Agent]  | |
|                  | +-------------------------------------------------------+ |
|                  |                                                           |
|                  | +------------------------------+ +----------------------+ |
|                  | | OPPORTUNITY LIST             | | OPPORTUNITY DETAIL   | |
|                  | | > AGM Planning Window        | | AGM Planning Window  | |
|                  | |   Apr-Aug                    | | Planning: Apr-Aug    | |
|                  | |   Priority: High             | | Audience: CS, IR     | |
|                  | |   Source: Manual             | | Offer: AGM stack     | |
|                  | |                              | | Pillars: Live, Sync  | |
|                  | |   Festive Activation         | |                      | |
|                  | |   Jul-Sep planning           | | Manual Zlicc note:   | |
|                  | |   Source: AI + Manual        | | Planning starts much | |
|                  | |                              | | earlier than public  | |
|                  | |   Fintech Exhibition Cycle   | | event dates suggest. | |
|                  | |   Priority: Medium           | |                      | |
|                  | |                              | | [Create Campaign]    | |
|                  | |                              | | [Edit] [Set Reminder]| |
|                  | +------------------------------+ +----------------------+ |
|                  |                                                           |
|                  | +-------------------------------------------------------+ |
|                  | | REMINDERS                                             | |
|                  | | 90 days before: create campaign brief                 | |
|                  | | 60 days before: build prospect list                   | |
|                  | | 45 days before: publish landing page                  | |
|                  | | 30 days before: follow-up warm leads                  | |
|                  | +-------------------------------------------------------+ |
+------------------+-----------------------------------------------------------+
```

Primary actions:

- Add manual opportunity.
- Approve AI suggestion.
- Create campaign.
- Set reminders.
- Edit timing.

---

## 14. Landing Page Builder

Question answered:

How do we create and publish a campaign landing page without manual HTML upload?

```text
+------------------------------------------------------------------------------+
| Zlicc Growth Console                                      Search      Profile |
+------------------+-----------------------------------------------------------+
| NAVIGATION       | LANDING PAGE BUILDER                                      |
| > Landing Pages  | Campaign: Exhibition / Booth Intelligence                 |
|                  |                                                           |
|                  | +-------------------------------------------------------+ |
|                  | | BUILD FLOW                                            | |
|                  | | Campaign -> Template -> Draft -> Edit -> Preview      | |
|                  | | -> Approval -> Publish                                | |
|                  | +-------------------------------------------------------+ |
|                  |                                                           |
|                  | +------------------------------+ +----------------------+ |
|                  | | PAGE SECTIONS                | | SECTION EDITOR       | |
|                  | | > Hero                       | | Hero                 | |
|                  | |   Problem                    | | Headline             | |
|                  | |   Offer                      | | [Turn booth footfall | |
|                  | |   Use Cases                  | |  into intelligence] | |
|                  | |   Pillar Stack               | |                      | |
|                  | |   Proof                      | | Subheadline          | |
|                  | |   CTA                        | | [Capture, engage...] | |
|                  | |   Lead Form                  | |                      | |
|                  | |   WhatsApp CTA               | | [Regenerate Section] | |
|                  | |                              | | [Save Section]       | |
|                  | +------------------------------+ +----------------------+ |
|                  |                                                           |
|                  | +------------------------------+ +----------------------+ |
|                  | | ASSETS / PROOF               | | PREVIEW              | |
|                  | | [Attach proof asset]         | | [Desktop] [Mobile]   | |
|                  | | [Attach video]               | |                      | |
|                  | | [Attach deck download]       | | Page preview block   | |
|                  | | Permission warnings shown    | |                      | |
|                  | +------------------------------+ +----------------------+ |
|                  |                                                           |
|                  | +-------------------------------------------------------+ |
|                  | | ACTIONS                                               | |
|                  | | [Save Draft] [Submit for Approval] [Publish]          | |
|                  | | [Unpublish] [View Live URL]                           | |
|                  | +-------------------------------------------------------+ |
+------------------+-----------------------------------------------------------+
```

Primary actions:

- Choose template.
- Generate draft.
- Edit section.
- Attach proof.
- Preview.
- Submit for approval.
- Publish.

Template flexibility rule:

- V1 should use fixed premium templates with limited section rendering.
- Users can edit copy, swap images/video/proof, change CTA, configure forms, hide optional sections, and reorder approved section blocks where the template supports it.
- Users should not upload arbitrary HTML for normal campaigns.
- Users should not create fully free-form page layouts in V1 because that will slow quality control and publishing reliability.

---

## 15. Content Studio

Question answered:

What content is required for each campaign, and what is ready or blocked?

```text
+------------------------------------------------------------------------------+
| Zlicc Growth Console                                      Search      Profile |
+------------------+-----------------------------------------------------------+
| NAVIGATION       | CONTENT STUDIO                                            |
| > Studio         | Campaign: All    Status: All                              |
|                  |                                                           |
|                  | +-------------------------------------------------------+ |
|                  | | CONTENT CONTROLS                                     | |
|                  | | Campaign [All v] Channel [All v] Status [All v]       | |
|                  | | [Generate Content Pack] [Create Manually]             | |
|                  | +-------------------------------------------------------+ |
|                  |                                                           |
|                  | +-------------------------------------------------------+ |
|                  | | CONTENT CARDS                                        | |
|                  | +-------------------------------------------------------+ |
|                  | | AGM LinkedIn Carousel                                | |
|                  | | Channel: LinkedIn   Quality: 8.7   Status: Approved   | |
|                  | | CTA: View AGM capability page                         | |
|                  | | [Open] [Schedule] [Duplicate]                         | |
|                  | +-------------------------------------------------------+ |
|                  | | Exhibition Proof Post                                | |
|                  | | Channel: LinkedIn   Quality: 6.2   Status: Revision   | |
|                  | | Blocker: Needs proof asset                            | |
|                  | | [Open] [Assign Creative]                              | |
|                  | +-------------------------------------------------------+ |
|                  | | Agency Email Sequence                                | |
|                  | | Channel: Email      Quality: 8.1   Status: Review     | |
|                  | | [Open] [Submit Approval]                              | |
|                  | +-------------------------------------------------------+ |
|                  |                                                           |
|                  | +------------------------------+ +----------------------+ |
|                  | | QUALITY SUMMARY              | | CMO SUGGESTIONS      | |
|                  | | Approved: 18                  | | Create one proof-led | |
|                  | | Needs revision: 7             | | post for Exhibition. | |
|                  | | Blocked: 3                    | | Avoid generic AI copy| |
|                  | +------------------------------+ +----------------------+ |
+------------------+-----------------------------------------------------------+
```

Primary actions:

- Generate content pack.
- Open draft.
- Submit approval.
- Assign creative.
- Schedule.

---

## 16. LinkedIn Publishing Calendar

Question answered:

What are we posting on LinkedIn, when, and for which campaign?

```text
+------------------------------------------------------------------------------+
| Zlicc Growth Console                                      Search      Profile |
+------------------+-----------------------------------------------------------+
| NAVIGATION       | LINKEDIN PUBLISHING                                       |
| > LinkedIn Posts | Week view                                                 |
|                  |                                                           |
|                  | +-------------------------------------------------------+ |
|                  | | WEEK CONTROLS                                        | |
|                  | | [This Week] [Next Week] Campaign [All v]              | |
|                  | | [Add Post] [Generate Weekly Plan]                     | |
|                  | +-------------------------------------------------------+ |
|                  |                                                           |
|                  | +-------------------------------------------------------+ |
|                  | | WEEKLY POST PLAN                                     | |
|                  | +-------------------------------------------------------+ |
|                  | | Tue | Company Page | AGM Carousel       | Approved     | |
|                  | | Tue | Founder      | AGM POV Post       | Draft        | |
|                  | | Wed | Company Page | Exhibition Proof   | Blocked      | |
|                  | | Thu | Founder      | Agency Partner POV | Review       | |
|                  | | Sat | Company Page | Pulse Poll         | Scheduled    | |
|                  | +-------------------------------------------------------+ |
|                  |                                                           |
|                  | +------------------------------+ +----------------------+ |
|                  | | SELECTED POST                | | CALENDAR HEALTH      | |
|                  | | Format: Carousel             | | Posts this week: 5   | |
|                  | | Campaign: AGM                | | Campaign spread: OK  | |
|                  | | Status: Approved             | | One blocker found    | |
|                  | | [Preview] [Edit]             | | [Resolve]            | |
|                  | | [Mark Published Manually]    | |                      | |
|                  | +------------------------------+ +----------------------+ |
+------------------+-----------------------------------------------------------+
```

Primary actions:

- Generate weekly plan.
- Add post.
- Edit draft.
- Approve.
- Mark published manually.

---

## 17. Newsletter Engine

Question answered:

What monthly newsletter should be created for LinkedIn and email audiences?

```text
+------------------------------------------------------------------------------+
| Zlicc Growth Console                                      Search      Profile |
+------------------+-----------------------------------------------------------+
| NAVIGATION       | NEWSLETTERS                                               |
| > Newsletters    | Monthly cadence                                           |
|                  |                                                           |
|                  | +-------------------------------------------------------+ |
|                  | | NEWSLETTER PLAN                                      | |
|                  | | Month: June 2026                                      | |
|                  | | LinkedIn Newsletter: Draft                            | |
|                  | | Email Newsletter: Not started                         | |
|                  | | [Generate Edition] [Create Manually]                  | |
|                  | +-------------------------------------------------------+ |
|                  |                                                           |
|                  | +------------------------------+ +----------------------+ |
|                  | | EDITIONS                     | | EDITION DETAIL       | |
|                  | | > June: Event Intelligence   | | Audience: Warm leads | |
|                  | |   Type: LinkedIn             | | Theme: From event    | |
|                  | |   Status: Draft              | | attendance to data   | |
|                  | |                              | |                      | |
|                  | |   June: Agency Tech Notes    | | Sections:            | |
|                  | |   Type: Email                | | - Opening POV        | |
|                  | |   Status: Not started        | | - Proof story        | |
|                  | |                              | | - Campaign CTA       | |
|                  | |                              | |                      | |
|                  | |                              | | [Open Draft]         | |
|                  | |                              | | [Submit Approval]    | |
|                  | +------------------------------+ +----------------------+ |
|                  |                                                           |
|                  | +-------------------------------------------------------+ |
|                  | | REUSE SUGGESTIONS                                    | |
|                  | | Best AGM post, Exhibition proof asset, Pulse poll can | |
|                  | | be repurposed into this month's edition.              | |
|                  | +-------------------------------------------------------+ |
+------------------+-----------------------------------------------------------+
```

Primary actions:

- Generate edition.
- Open draft.
- Attach content.
- Submit approval.

---

## 18. Creative Production Desk

Question answered:

What needs to be produced, by whom, by when, and what is blocked?

```text
+------------------------------------------------------------------------------+
| Zlicc Growth Console                                      Search      Profile |
+------------------+-----------------------------------------------------------+
| NAVIGATION       | CREATIVE PRODUCTION DESK                                  |
| > Creative Desk  | Tasks: 31    Overdue: 4    Blocked: 3                    |
|                  |                                                           |
|                  | +-------------------------------------------------------+ |
|                  | | BOARD FILTERS                                        | |
|                  | | View [Board/List/Calendar] Owner [All v] Campaign [v] | |
|                  | | Asset Type [All v] Status [All v] Deadline [All v]    | |
|                  | | [Create Task] [Generate Brief]                        | |
|                  | +-------------------------------------------------------+ |
|                  |                                                           |
|                  | +----------+----------+----------+----------+----------+ |
|                  | | Briefed  | In Prog  | Uploaded | Revision | Approved | |
|                  | +----------+----------+----------+----------+----------+ |
|                  | | AGM      | Agency   | Pulse    | Exhibit  | AGM deck | |
|                  | | carousel | video    | image    | proof    |          | |
|                  | | due Wed  | due Fri  | review   | blocked  |          | |
|                  | |          |          |          |          |          | |
|                  | | Booth LP |          |          |          |          | |
|                  | | hero     |          |          |          |          | |
|                  | +----------+----------+----------+----------+----------+ |
|                  |                                                           |
|                  | +------------------------------+ +----------------------+ |
|                  | | SELECTED TASK                | | BRIEF / FILES        | |
|                  | | Exhibition proof carousel     | | Audience: Brands     | |
|                  | | Owner: Designer               | | Format: LinkedIn doc | |
|                  | | Deadline: Today               | | References attached  | |
|                  | | Status: Needs Revision        | | Uploads: v1, v2      | |
|                  | |                              | | [Upload New Version] | |
|                  | | [Request Changes] [Approve]  | | [Open Files]         | |
|                  | +------------------------------+ +----------------------+ |
+------------------+-----------------------------------------------------------+
```

Primary actions:

- Generate brief.
- Assign task.
- Upload asset.
- Request changes.
- Approve.

View mode rule:

- The default view should be a kanban board because creative production moves through visible stages: briefed, in progress, uploaded, revision, approved.
- A table/list view is also required for practical operations such as sorting by deadline, owner, campaign, asset type, overdue status, and bulk assignment.
- A lightweight calendar view can be added for deadline visibility, but board and list are the V1 priority.

---

## 19. Asset Library / Proof Vault

Question answered:

Which approved assets and proof can be reused safely?

```text
+------------------------------------------------------------------------------+
| Zlicc Growth Console                                      Search      Profile |
+------------------+-----------------------------------------------------------+
| NAVIGATION       | ASSET LIBRARY / PROOF VAULT                               |
| > Assets         | Assets: 842    Public approved: 118    Internal: 366      |
|                  |                                                           |
|                  | +-------------------------------------------------------+ |
|                  | | SEARCH AND FILTERS                                   | |
|                  | | Search [                                      ]        | |
|                  | | Type [All v] Pillar [All v] Permission [All v]        | |
|                  | | Campaign [All v] Industry [All v]                     | |
|                  | | [Upload Asset] [Create Proof Asset]                   | |
|                  | +-------------------------------------------------------+ |
|                  |                                                           |
|                  | +-------------------------------------------------------+ |
|                  | | ASSET GRID / LIST                                    | |
|                  | +-------------------------------------------------------+ |
|                  | | AGM webcast deck       Public approved   Live/Sync     | |
|                  | | Pulse activity images  Internal only     Pulse         | |
|                  | | Booth demo video       Permission needed XR/Sync       | |
|                  | | AI summary screenshot  Public approved   AI            | |
|                  | +-------------------------------------------------------+ |
|                  |                                                           |
|                  | +------------------------------+ +----------------------+ |
|                  | | SELECTED ASSET               | | USAGE                | |
|                  | | Booth demo video              | | Used in: 2 drafts    | |
|                  | | Permission: Client required   | | Suggested for:       | |
|                  | | Pillars: XR, Sync             | | Exhibition campaign  | |
|                  | | Use case: Booth intelligence  | |                      | |
|                  | | [Request Permission]          | | [Attach to Campaign] | |
|                  | | [Mark Internal Only]          | | [Open File]          | |
|                  | +------------------------------+ +----------------------+ |
+------------------+-----------------------------------------------------------+
```

Primary actions:

- Upload asset.
- Tag proof.
- Attach to campaign.
- Request permission.
- Mark internal-only.

---

## 20. Email Campaigns

Question answered:

Which email sequences are ready, running, or blocked?

```text
+------------------------------------------------------------------------------+
| Zlicc Growth Console                                      Search      Profile |
+------------------+-----------------------------------------------------------+
| NAVIGATION       | EMAIL CAMPAIGNS                                           |
| > Email          | Active sequences: 3    Pending approval: 2                |
|                  |                                                           |
|                  | +-------------------------------------------------------+ |
|                  | | EMAIL CONTROLS                                       | |
|                  | | Campaign [All v] Status [All v] Sender [All v]        | |
|                  | | [Create Sequence] [Generate Sequence] [Test Send]     | |
|                  | +-------------------------------------------------------+ |
|                  |                                                           |
|                  | +-------------------------------------------------------+ |
|                  | | SEQUENCES                                             | |
|                  | +-------------------------------------------------------+ |
|                  | | AGM Outreach      Approved  184 recipients  Running   | |
|                  | | Agency Nurture    Review    142 recipients  Draft     | |
|                  | | Exhibition Stack  Blocked   96 recipients   Proof due | |
|                  | +-------------------------------------------------------+ |
|                  |                                                           |
|                  | +------------------------------+ +----------------------+ |
|                  | | SELECTED SEQUENCE           | | PERFORMANCE          | |
|                  | | AGM Outreach                 | | Sent: 184            | |
|                  | | Reply-to: founder@zlicc.com  | | Opened: 62           | |
|                  | | Steps: 3                     | | Clicked: 19          | |
|                  | | Approval: Approved           | | Replies: 7           | |
|                  | | [Open Steps] [Pause]         | | Bounces: 4           | |
|                  | | [Add Recipients]             | | Unsubs: 2            | |
|                  | +------------------------------+ +----------------------+ |
+------------------+-----------------------------------------------------------+
```

Primary actions:

- Create/generate sequence.
- Review steps.
- Test send.
- Add recipients.
- Pause.

---

## 21. WhatsApp Assistant

Question answered:

Which WhatsApp conversations need the bot, qualification, or human handoff?

```text
+------------------------------------------------------------------------------+
| Zlicc Growth Console                                      Search      Profile |
+------------------+-----------------------------------------------------------+
| NAVIGATION       | WHATSAPP ASSISTANT                                        |
| > WhatsApp       | Active sessions: 18    Handoffs: 3    Opt-outs: 2         |
|                  |                                                           |
|                  | +-------------------------------------------------------+ |
|                  | | SESSION FILTERS                                      | |
|                  | | [All] [Bot Active] [Needs Handoff] [High Intent]      | |
|                  | | [Opt-out] [Low Confidence]                            | |
|                  | +-------------------------------------------------------+ |
|                  |                                                           |
|                  | +------------------------------+ +----------------------+ |
|                  | | CONVERSATIONS                | | CONVERSATION DETAIL  | |
|                  | | > Rahul Mehta                | | Rahul Mehta          | |
|                  | |   Asked for pricing          | | Campaign: Pulse      | |
|                  | |   Handoff required           | | Intent: Pricing      | |
|                  | |                              | | Confidence: 91       | |
|                  | |   Priya S.                   | |                      | |
|                  | |   Asked for deck             | | Last bot response:   | |
|                  | |   Bot handled                | | Shared Pulse landing | |
|                  | |                              | | page and asked event | |
|                  | |   Unknown number             | | timeline.            | |
|                  | |   Low confidence             | |                      | |
|                  | |                              | | [Assign Human]       | |
|                  | |                              | | [Open Lead]          | |
|                  | +------------------------------+ +----------------------+ |
|                  |                                                           |
|                  | +-------------------------------------------------------+ |
|                  | | BOT GUARDRAILS                                       | |
|                  | | Allowed: approved links, basic offer details,          | |
|                  | | qualifying questions                                  | |
|                  | | Handoff: pricing, proposal, complex brief, low confidence |
|                  | +-------------------------------------------------------+ |
+------------------+-----------------------------------------------------------+
```

Primary actions:

- Assign human.
- Open lead.
- Review bot transcript.
- Mark handled.
- Update opt-out.

---

## 22. Reply Intelligence

Question answered:

Which email and WhatsApp replies changed lead priority?

```text
+------------------------------------------------------------------------------+
| Zlicc Growth Console                                      Search      Profile |
+------------------+-----------------------------------------------------------+
| NAVIGATION       | REPLY INTELLIGENCE                                        |
| > Replies        | New replies: 12    Hot: 5    Needs owner: 4               |
|                  |                                                           |
|                  | +-------------------------------------------------------+ |
|                  | | REPLY FILTERS                                        | |
|                  | | Channel [All v] Intent [All v] Campaign [All v]       | |
|                  | | [Interested] [Meeting] [Proposal] [Unsubscribe]       | |
|                  | +-------------------------------------------------------+ |
|                  |                                                           |
|                  | +------------------------------+ +----------------------+ |
|                  | | REPLY LIST                   | | REPLY DETAIL         | |
|                  | | > Priya S.                   | | Intent: Meeting      | |
|                  | |   Outlook                    | | Confidence: 93       | |
|                  | |   Meeting intent             | | Score delta: +25     | |
|                  | |                              | |                      | |
|                  | |   Rahul Mehta                | | Summary: Asked for   | |
|                  | |   WhatsApp                   | | more details and a   | |
|                  | |   Pricing question           | | short call this week.| |
|                  | |                              | |                      | |
|                  | |   Agency founder             | | Recommended action:  | |
|                  | |   Outlook                    | | Book meeting.        | |
|                  | |   Send deck                  | |                      | |
|                  | |                              | | [Create Task]        | |
|                  | |                              | | [Open Lead]          | |
|                  | +------------------------------+ +----------------------+ |
|                  |                                                           |
|                  | +-------------------------------------------------------+ |
|                  | | BULK ACTIONS                                          | |
|                  | | [Assign Owners] [Mark Handled] [Create Follow-ups]    | |
|                  | +-------------------------------------------------------+ |
+------------------+-----------------------------------------------------------+
```

Primary actions:

- Open reply.
- Create task.
- Assign owner.
- Update lead.
- Mark handled.

---

## 23. CMO Brain

Question answered:

What is the CMO Brain recommending and why?

```text
+------------------------------------------------------------------------------+
| Zlicc Growth Console                                      Search      Profile |
+------------------+-----------------------------------------------------------+
| NAVIGATION       | CMO BRAIN                                                 |
| > CMO Brain      | Current weekly mode: Aggressive prospecting               |
|                  |                                                           |
|                  | +-------------------------------------------------------+ |
|                  | | WEEKLY STRATEGIC SUMMARY                             | |
|                  | | Priority: AGM and investor communication lane.         | |
|                  | | Secondary: Exhibition stack only after proof assets.   | |
|                  | | Hold: New fourth campaign until capacity opens.        | |
|                  | | [Apply to Portfolio] [Edit Strategy]                  | |
|                  | +-------------------------------------------------------+ |
|                  |                                                           |
|                  | +------------------------------+ +----------------------+ |
|                  | | RECOMMENDATIONS              | | EXPLANATION          | |
|                  | | > Increase AGM follow-up      | | Why: high reply rate,| |
|                  | |   Priority: High              | | current timing,      | |
|                  | |                              | | strong offer fit.    | |
|                  | |   Pause Exhibition scale      | |                      | |
|                  | |   Priority: Medium            | | Risk: proof gap      | |
|                  | |                              | | weakens conversion.  | |
|                  | |   Agency LinkedIn nurture     | |                      | |
|                  | |   Priority: Medium            | | [Open Evidence]      | |
|                  | +------------------------------+ +----------------------+ |
|                  |                                                           |
|                  | +-------------------------------------------------------+ |
|                  | | DECISION ACTIONS                                      | |
|                  | | [Approve Recommendation] [Edit] [Reject]              | |
|                  | | [Create Tasks] [Generate Report]                      | |
|                  | +-------------------------------------------------------+ |
+------------------+-----------------------------------------------------------+
```

Primary actions:

- Approve recommendation.
- Edit strategy.
- Create tasks.
- Generate report.

CMO Brain operating model:

- The CMO Brain should have a dedicated screen for weekly strategy, recommendations, evidence, and auditability.
- Its most important recommendations should also appear contextually inside Today, Campaign Portfolio, Lead Detail, Landing Pages, Content Studio, Creative Desk, Reply Intelligence, and Analytics.
- The CMO Brain should not behave like an open-ended chatbot as the main UX. It should behave like a decision layer: recommendation, reason, evidence, risk, next action, approval.
- The dedicated CMO Brain screen is the strategy room; contextual CMO panels are the operating assistant inside each workflow.
- CMO Brain can suggest, prioritize, audit, and create tasks; public publishing, sensitive claims, campaign activation, pricing, and client references still require human approval.

Continuous learning rule:

- The system should preserve learning signals from approvals, edits, rejections, manual overrides, campaign performance, replies, WhatsApp handoffs, LinkedIn outcomes, content quality scores, and creative revision cycles.
- Learning should update future recommendations through stored patterns and approved knowledge, not by silently changing core strategy without review.
- The user should be able to see why a recommendation changed: performance evidence, reply pattern, campaign result, approval history, or manual Zlicc instruction.
- Admin/CMO Brain views should expose important learning logs so the team can correct the system when it learns the wrong pattern.

---

## 24. Agent Ops

Question answered:

What are the specialist agents doing, what did they output, and what needs review?

```text
+------------------------------------------------------------------------------+
| Zlicc Growth Console                                      Search      Profile |
+------------------+-----------------------------------------------------------+
| NAVIGATION       | AGENT OPS                                                 |
| > Agent Ops      | Runs today: 48    Failed: 2    Approval needed: 9         |
|                  |                                                           |
|                  | +-------------------------------------------------------+ |
|                  | | AGENT STATUS                                          | |
|                  | +-------------------------------------------------------+ |
|                  | | Agent                 Last Run      Status   Review    | |
|                  | | Market Research       09:00         Done     2 items   | |
|                  | | Prospecting           09:30         Running  -         | |
|                  | | Content Strategy      10:10         Done     4 items   | |
|                  | | Creative Briefing     10:25         Done     1 item    | |
|                  | | Reply Intelligence    Live          Done     2 hot     | |
|                  | | WhatsApp Assistant    Live          Active   3 handoff | |
|                  | | Analytics             Friday only   Idle     -         | |
|                  | | Compliance            Live          Done     0 blocked | |
|                  | +-------------------------------------------------------+ |
|                  |                                                           |
|                  | +------------------------------+ +----------------------+ |
|                  | | SELECTED RUN                 | | OUTPUT PREVIEW       | |
|                  | | Agent: Content Strategy       | | Suggested 5 posts    | |
|                  | | Trigger: Campaign content     | | for AGM lane.        | |
|                  | | Quality: 8.3                  | |                      | |
|                  | | Cost est: $0.08               | | [Open Output]        | |
|                  | | Status: Needs approval        | | [Approve] [Revise]   | |
|                  | +------------------------------+ +----------------------+ |
+------------------+-----------------------------------------------------------+
```

Primary actions:

- Review output.
- Approve.
- Request revision.
- Re-run.
- Disable agent.

---

## 25. Analytics

Question answered:

What is working, what is weak, and what should change next?

```text
+------------------------------------------------------------------------------+
| Zlicc Growth Console                                      Search      Profile |
+------------------+-----------------------------------------------------------+
| NAVIGATION       | ANALYTICS                                                 |
| > Analytics      | Period: This week                                         |
|                  |                                                           |
|                  | +-------------------------------------------------------+ |
|                  | | CMO ANALYTICS SUMMARY                                | |
|                  | | AGM lane is producing the highest meeting intent.      | |
|                  | | Exhibition lane has weak conversion due to proof gap.  | |
|                  | | Agency lane is warming through LinkedIn, not email.    | |
|                  | | [Generate Weekly Report] [Export]                     | |
|                  | +-------------------------------------------------------+ |
|                  |                                                           |
|                  | +-------------+ +-------------+ +-------------+ +-------+ |
|                  | | Leads Added | | Replies     | | Meetings    | | LP CVR| |
|                  | | 184         | | 21          | | 5           | | 7.2%  | |
|                  | +-------------+ +-------------+ +-------------+ +-------+ |
|                  |                                                           |
|                  | +------------------------------+ +----------------------+ |
|                  | | CAMPAIGN PERFORMANCE         | | CHANNEL PERFORMANCE  | |
|                  | | AGM: Strong                  | | Email: good replies  | |
|                  | | Exhibition: Blocked          | | WhatsApp: hot intent | |
|                  | | Agency: Watch                | | LinkedIn: warming    | |
|                  | |                              | | Landing: improving   | |
|                  | +------------------------------+ +----------------------+ |
|                  |                                                           |
|                  | +------------------------------+ +----------------------+ |
|                  | | WARM SIGNALS                 | | NEXT RECOMMENDATION  | |
|                  | | Deck clicks: 42              | | Follow up 14 AGM     | |
|                  | | Landing visits: 126          | | leads. Do not scale  | |
|                  | | WA replies: 9                | | Exhibition until     | |
|                  | | Outlook replies: 12          | | proof is approved.   | |
|                  | +------------------------------+ +----------------------+ |
+------------------+-----------------------------------------------------------+
```

Primary actions:

- Generate weekly report.
- Export.
- Open campaign analytics.
- Open hot leads.

---

## 26. Admin / Integrations

Question answered:

Are the systems, APIs, users, and permissions healthy?

```text
+------------------------------------------------------------------------------+
| Zlicc Growth Console                                      Search      Profile |
+------------------+-----------------------------------------------------------+
| NAVIGATION       | ADMIN / INTEGRATIONS                                      |
| > Admin          | System health                                             |
|                  |                                                           |
|                  | +-------------------------------------------------------+ |
|                  | | INTEGRATION STATUS                                   | |
|                  | +-------------------------------------------------------+ |
|                  | | OpenAI API          Connected     Usage: $42 / $100    | |
|                  | | Apollo              Connected     Credits: 640 left    | |
|                  | | SendGrid            Connected     Webhooks OK          | |
|                  | | Microsoft Graph     Connected     Last sync: 5 min     | |
|                  | | WhatsApp API        Warning       2 webhook failures   | |
|                  | | S3 Storage          Connected     Uploads OK           | |
|                  | | Make Webhooks       Optional      3 active             | |
|                  | +-------------------------------------------------------+ |
|                  |                                                           |
|                  | +------------------------------+ +----------------------+ |
|                  | | USERS / ROLES                | | AUDIT LOG            | |
|                  | | Admin: 1                     | | Approval updated     | |
|                  | | Founder: 1                   | | SendGrid key changed | |
|                  | | LinkedIn Ops: 2              | | WA handoff assigned  | |
|                  | | Creative: 4                  | | Agent config edited  | |
|                  | | Sales: 2                     | |                      | |
|                  | | [Manage Users]               | | [Open Audit Logs]    | |
|                  | +------------------------------+ +----------------------+ |
|                  |                                                           |
|                  | +-------------------------------------------------------+ |
|                  | | SYSTEM ACTIONS                                       | |
|                  | | [Test Integrations] [View Errors] [Manage API Keys]   | |
|                  | | [Spend Dashboard] [Backup Status] [Deployment Runbook]| |
|                  | +-------------------------------------------------------+ |
+------------------+-----------------------------------------------------------+
```

Primary actions:

- Test integration.
- Manage keys.
- Manage users.
- View audit logs.
- View errors.
- Check backup status.

Spend and usage rule:

- API and integration spend should not appear on the general Today screen for all users.
- Admin / Integrations should include a dedicated spend dashboard for OpenAI, Apollo credits, WhatsApp conversations, SendGrid volume, storage, and Make operations if used.
- Spend should be visible by provider, feature, agent, campaign, and month wherever possible.
- The dashboard should show usage trend, budget limit, alerts, failed runs, and unusually expensive workflows.

---

## 27. Review Order

Recommended review sequence:

1. Today / Command Centre.
2. Lead Detail.
3. Campaign Portfolio.
4. Quick Capture.
5. LinkedIn Workbench.
6. Seasonal Calendar.
7. Landing Page Builder.
8. Content Studio.
9. Creative Production Desk.
10. Reply Intelligence.
11. Agent Ops.
12. Analytics.
13. Admin / Integrations.

Reason:

This order starts with daily operation, then lead decisions, then campaign planning, then execution, then intelligence and admin.

---

## 28. Resolved UX Decisions

1. The app starts with Today for all users.
2. Today is role-specific. Each user sees their own tasks, queues, trackers, and actionable context.
3. Approvals live as a dedicated module and also appear contextually inside each workflow.
4. CMO Brain has a dedicated strategy and audit screen, but its recommendations also appear contextually across the system.
5. CMO Brain should operate as a decision layer, not primarily as a chatbot.
6. LinkedIn Operators see assigned task context only, with enough campaign/offer context to act correctly. They do not see strategic campaign performance.
7. Creative Production Desk uses kanban board as the default view, with table/list view required for deadlines, sorting, filtering, and bulk operations.
8. Landing Pages use fixed premium templates with limited section rendering: editable copy, media, CTA, proof, forms, optional section visibility, and approved section reordering.
9. Existing customers stay in the audience/prospecting area in V1 and are used for communication, education, cross-sell, upsell, and reactivation campaigns.
10. API and integration spend lives in Admin / Integrations through a dedicated spend dashboard, not on the general Today screen.
11. Continuous learning is required for CMO Brain and specialist agents, based on approvals, edits, overrides, replies, performance, quality scores, and campaign outcomes.

---

## 29. Remaining UX Decisions

1. Exact visual density for the command screens: compact operations console versus slightly more spacious executive dashboard.
2. Whether creative calendar view ships in V1 or follows after board/list views.
3. Whether admin spend alerts should also create tasks for the Admin role.
4. Whether the CMO Brain learning log should appear inside CMO Brain only or also inside Agent Ops.
