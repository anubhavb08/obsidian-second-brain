# Zlicc Growth Console UI Mockup Direction

Version: 0.2  
Created: 2026-05-22  
Updated: 2026-05-22  
Status: High-fidelity UI mockup brief  
Source documents: `Zlicc_Growth_Console_Low_Fidelity_Wireframes.md`, `Zlicc_Growth_Console_V1_PRD.md`, `Zlicc_Growth_Console_Engineering_Backlog.md`

---

## 1. Purpose

This document defines the high-fidelity UI mockup direction for Zlicc Growth Console.

The low-fidelity UX blueprint defines what each screen does. This document defines how the product should feel, how UI components should behave, which screens should be mocked first, and what the clickable prototype should demonstrate.

The goal is to create a premium operational console for growth, not a generic CRM dashboard and not a marketing website.

---

## 2. Product Feel

Zlicc Growth Console should feel like:

- A focused CMO command center.
- A high-trust enterprise SaaS tool.
- A daily operating surface for prospecting, campaigns, content, outreach, approvals, and analytics.
- Calm, dense, and highly scannable.
- Intelligent without looking gimmicky.
- Premium without feeling decorative.

It should not feel like:

- A traditional sales CRM clone.
- A colorful startup dashboard with decorative cards everywhere.
- A landing page.
- A chatbot-first product.
- A creative portfolio website.
- A tool that hides decisions behind AI magic.

Design principle:

> The UI should make Zlicc's growth operation feel controlled, visible, and decisive.

---

## 3. Visual Direction

### 3.1 Overall Style

Use a restrained B2B console style:

- Dark navigation sidebar.
- Light main workspace.
- Compact panels.
- Strong tables and queues.
- Clear status chips.
- Minimal decorative elements.
- High information density with enough whitespace to avoid fatigue.
- CMO/AI recommendations presented as structured decision cards, not chat bubbles.

Avoid:

- Gradient orb backgrounds.
- Oversized hero sections.
- Heavy illustrations.
- Over-rounded cards.
- Decorative glassmorphism.
- One-note purple/blue theme.
- Marketing-site composition.

### 3.2 Color Palette

Recommended palette:

| Token | Usage | Hex |
| --- | --- | --- |
| `ink-950` | Sidebar, primary text on dark | `#101418` |
| `ink-900` | Dark surfaces | `#171C22` |
| `slate-700` | Secondary text | `#4A5565` |
| `slate-500` | Muted labels | `#6B7280` |
| `slate-200` | Borders | `#D8DEE8` |
| `slate-100` | Page background | `#F4F6F8` |
| `white` | Main panels | `#FFFFFF` |
| `cyan-600` | Zlicc primary accent | `#00A8C8` |
| `cyan-50` | Soft accent surface | `#E9FAFD` |
| `amber-500` | Warning, pending, attention | `#D98A00` |
| `green-600` | Approved, healthy, success | `#14804A` |
| `red-600` | Risk, blocked, failed | `#C93434` |
| `violet-600` | AI/agent signal, sparingly | `#6D5BD0` |

Rules:

- Cyan is the Zlicc accent, not the whole interface.
- Use amber/green/red for operational state clarity.
- Use violet only to tag AI/agent items when helpful.
- Main working areas should remain light and quiet.
- Dark mode is not required for V1 mockups; the app shell can use a dark sidebar.

### 3.3 Typography

Recommended typography:

- Primary UI font: Inter, Geist, or similar modern SaaS font.
- Numbers and metrics should use tabular numerals where possible.
- Avoid display-style type except for empty states or onboarding screens.

Suggested scale:

| Token | Size | Usage |
| --- | --- | --- |
| `display-sm` | 28px / 36px | Rare page-level emphasis |
| `heading-lg` | 22px / 30px | Screen titles |
| `heading-md` | 18px / 26px | Panel titles |
| `body-md` | 14px / 22px | Default UI text |
| `body-sm` | 13px / 20px | Dense tables, metadata |
| `caption` | 12px / 16px | Labels, badges, timestamps |

Rules:

- Do not scale typography based on viewport width.
- No negative letter spacing.
- Use smaller, tighter headings inside dashboards, queues, and panels.
- Text must not overflow buttons, chips, table cells, or cards.

### 3.4 Spacing And Shape

Recommended layout tokens:

- Page margin: 24px desktop.
- Panel padding: 16px to 20px.
- Dense row height: 44px to 52px.
- Card radius: 8px maximum.
- Button radius: 6px.
- Chip radius: 999px only for small status chips.
- Border color: `slate-200`.

Rules:

- Avoid cards inside cards.
- Use panels for page areas and cards only for repeated items, tasks, approvals, and selected details.
- Tables and queues should remain stable when labels, badges, or statuses change.

---

## 4. Navigation Model

All users start on `Today`.

The left navigation should be grouped as:

- Command: Today, Approvals, Tasks.
- Prospecting: Leads, Quick Capture, Apollo, LinkedIn, Customers.
- Campaigns: Portfolio, Calendar, Landing Pages.
- Content: Studio, LinkedIn Posts, Newsletters, Creative Desk, Assets.
- Outreach: Email, WhatsApp, Replies.
- Intelligence: CMO Brain, Agent Ops, Analytics.
- Admin: Integrations, Users, Settings, Audit Logs.

Role behavior:

- Founder sees all major modules.
- LinkedIn Operator sees Today, Tasks, LinkedIn, limited Leads, and limited profile/settings.
- Creative Team sees Today, Tasks, Creative Desk, Assets, limited Campaign/Content context.
- Sales/Handoff Owner sees Today, Tasks, Leads, Replies, WhatsApp handoffs, limited Campaign context.
- Admin sees Admin modules plus system health.

---

## 5. Component System

### 5.1 Buttons

Button types:

- Primary: main action on a screen.
- Secondary: normal action.
- Ghost: low-emphasis action.
- Danger: destructive or risky action.
- Icon button: compact actions using lucide icons.

Rules:

- Use icons for common tool actions such as search, filter, copy, open, edit, approve, reject, upload, calendar, settings, refresh, alert, external link.
- Do not use a text button where a familiar icon with tooltip is clearer.
- Every icon-only action needs a tooltip.

### 5.2 Status Chips

Use chips for:

- Lead stage.
- Campaign status.
- Campaign health.
- Approval status.
- Agent state.
- Content status.
- Consent state.
- Risk level.

Recommended chip mapping:

| State | Color |
| --- | --- |
| Active, healthy, approved | Green |
| Pending, review, scheduled | Amber |
| Blocked, failed, high risk | Red |
| Draft, idle, neutral | Slate |
| AI/agent-generated | Violet |
| Zlicc accent/actionable | Cyan |

### 5.3 Tables And Queues

Most operational screens should use tables or split queues.

Required table behavior:

- Search.
- Filters.
- Sort.
- Bulk select where useful.
- Row actions.
- Empty state.
- Loading state.
- Error state.

High priority tables:

- Leads.
- Tasks.
- Approvals.
- LinkedIn queue.
- Agent runs.
- Outreach messages.
- Reply Intelligence.
- Assets.

### 5.4 CMO Recommendation Panel

This is a key component across the app.

Structure:

- Recommendation headline.
- Reason.
- Evidence.
- Risk.
- Next action.
- Confidence.
- Approval requirement.
- Action buttons.

Example structure:

```text
CMO Recommendation
Prioritize AGM follow-ups today.

Why:
14 warm leads clicked the deck or replied in the last 72 hours.

Risk:
Do not scale Exhibition campaign until proof assets are approved.

Actions:
[Approve] [Create Tasks] [Edit] [Reject]
```

Rules:

- Do not present CMO Brain as a chatbot by default.
- Use structured cards/panels.
- Always show why the recommendation exists.
- Always show what human action is expected.

### 5.5 Approval Card

Structure:

- Item type.
- Title.
- Campaign.
- Owner.
- Risk level.
- Due date.
- Current status.
- Preview.
- Reason approval is required.
- Actions: approve, edit, reject, request revision.

### 5.6 Lead Score Indicator

Use a compact score badge plus reason.

Score bands:

- 80 to 100: Hot.
- 60 to 79: Warm.
- 40 to 59: Watch.
- 0 to 39: Low.
- Suppressed: no outreach.

Visual:

- Score badge.
- Band label.
- One-line reason.
- Last signal.

### 5.7 Campaign Lane Card

Structure:

- Campaign name.
- Tier.
- Audience.
- Offer.
- Pillar stack.
- Status.
- Health.
- Landing page status.
- Content status.
- Outreach status.
- Replies, meetings, warm leads.
- Blocker if any.
- Actions.

### 5.8 Agent State Row

Structure:

- Agent name.
- Last run.
- Status.
- Output count.
- Review needed.
- Quality score.
- Cost estimate.
- Error if any.

Agent states:

- Running.
- Done.
- Needs review.
- Failed.
- Disabled.
- Live.
- Idle.

### 5.9 Creative Task Card

Structure:

- Asset type.
- Campaign.
- Owner.
- Deadline.
- Status.
- Brief completeness.
- Upload count.
- Review state.
- Blocker.

Views:

- Board view default.
- List/table view required.
- Calendar view optional after V1 board/list.

---

## 6. Screen Mockup Priority

### Phase 1 Mockups: Core Command System

These screens should be designed first because they define the product's daily operating feel:

1. Today / Command Centre.
2. Approvals.
3. Campaign Portfolio.
4. Lead Detail.
5. CMO Brain.
6. Agent Ops.

### Phase 2 Mockups: Execution Workflows

1. Quick Capture.
2. LinkedIn Workbench.
3. Seasonal Calendar.
4. Landing Page Builder.
5. Content Studio.
6. Creative Production Desk.
7. Reply Intelligence.
8. Analytics.
9. Admin / Integrations.

### Phase 3 Mockups: Supporting Views

1. Leads list.
2. Apollo import/enrichment.
3. Email sequences.
4. WhatsApp Assistant.
5. Asset Library / Proof Vault.
6. Newsletters.
7. Tasks.
8. Settings.

---

## 7. High-Fidelity Screen Briefs

### 7.1 Today / Command Centre

Purpose:

- Give every user their daily action list and operating context.

Founder version should show:

- CMO priority panel.
- Hot replies.
- Approvals.
- WhatsApp handoffs.
- Tasks.
- Three active campaign lanes.
- Hot leads.
- Work queues.
- Weekly learning.

Role-specific versions:

- LinkedIn Operator: assigned LinkedIn tasks, suggested copy queue, overdue items, replies to log.
- Creative Team: assigned assets, deadlines, revision requests, upload actions, blocked tasks.
- Sales/Handoff: hot replies, WA handoffs, meeting/proposal requests, follow-up tasks.
- Admin: integration health, failed webhooks, API usage alerts, backup status, user/access issues.

Mockup notes:

- This screen should feel like the app's cockpit.
- Use dense metric cards, not large decorative cards.
- CMO panel should be visually distinct but not oversized.

### 7.2 Approvals

Purpose:

- Show everything waiting for human approval in one place.

Must include:

- Filters by content, landing page, email, WhatsApp, campaigns, proof, claims, high risk.
- Queue list.
- Selected item preview.
- Risk reason.
- Approval actions.
- Comments/revision history.

Mockup notes:

- Split layout: queue on left, selected item on right.
- High-risk items must be visually obvious.
- Approvals also remain contextual inside source workflows.

### 7.3 Campaign Portfolio

Purpose:

- Manage up to three active campaign lanes.

Must include:

- Active lane capacity indicator: `3 / 3 active`.
- Campaign lane cards.
- Draft/scheduled/paused/completed sections.
- Blockers.
- CMO recommendation.
- Add leads, open content, review landing page, pause campaign actions.

Mockup notes:

- Campaign lane cards should be scannable.
- Health states should be clear: Good, Watch, Blocked.
- Do not over-visualize charts here; analytics has its own screen.

### 7.4 Lead Detail

Purpose:

- Show full context and next-best action for one lead.

Must include:

- Contact and company header.
- Lead score and reason.
- Stage.
- Recommended offer and pillar stack.
- Next-best action.
- Timeline.
- Warm signals.
- Tasks.
- Outreach history.
- LinkedIn notes.
- CMO recommendation panel.

Mockup notes:

- Use a two-column layout: main timeline/detail and right-side decision panel.
- Score should be compact but prominent.
- Suppression/consent warnings must be impossible to miss.

### 7.5 CMO Brain

Purpose:

- Strategy, audit, learning, and decision review.

Must include:

- Weekly strategic summary.
- Recommendations list.
- Evidence panel.
- Risks.
- Learning log.
- Decision actions.
- Apply to portfolio.
- Create tasks.

Mockup notes:

- The CMO Brain should look like an executive strategy room inside the console.
- It should not be a chat-only interface.
- It should show recommendation changes and why they changed.

### 7.6 Agent Ops

Purpose:

- Monitor specialist agent runs, outputs, errors, approvals, and costs.

Must include:

- Agent status table.
- Selected run detail.
- Output preview.
- Approval actions.
- Re-run.
- Disable agent.
- Cost estimate.
- Errors.

Mockup notes:

- This screen can be more technical than CMO Brain.
- It should reassure the user that AI work is logged and inspectable.

### 7.7 Quick Capture

Purpose:

- Convert informal personal WhatsApp/call/referral details into structured lead records.

Must include:

- Contact name.
- Company.
- Mobile/WhatsApp.
- Email.
- LinkedIn URL.
- Source.
- Brief notes.
- File/link upload.
- Follow-up date.
- Save and ask CMO Brain.

Mockup notes:

- This should be fast and low-friction.
- Keep it as a short form, not a CRM data-entry marathon.

### 7.8 LinkedIn Workbench

Purpose:

- Help LinkedIn Operators execute assigned manual actions.

Must include:

- Today, overdue, high priority, replied, snoozed tabs.
- Task list.
- Task detail.
- Suggested copy.
- Open LinkedIn action.
- Log outcome.

Visibility:

- Show assigned task context only.
- Do not show strategic campaign performance.

Mockup notes:

- The operator should feel guided, not strategic.
- Copy and logging should be one click away.

### 7.9 Seasonal Calendar

Purpose:

- Manage AI-suggested and manually entered opportunity windows.

Must include:

- Calendar/list toggle.
- Manual opportunity form.
- AI suggestions pending approval.
- Planning window.
- Event window.
- Reminders.
- Linked campaign.

Mockup notes:

- Manual Zlicc entries should look first-class, not secondary.
- AI suggestions should be pending until approved.

### 7.10 Landing Page Builder

Purpose:

- Generate and publish campaign landing pages without manual HTML upload.

Must include:

- Campaign to template to draft to edit to preview to approval to publish flow.
- Section list.
- Section editor.
- Asset/proof attachment.
- Desktop/mobile preview.
- WhatsApp CTA.
- Lead form setup.

Flexibility:

- Fixed premium templates.
- Limited section rendering.
- Users can edit copy, swap media/proof, hide optional sections, reorder approved section blocks, configure CTA/form.
- No arbitrary HTML upload in V1.

Mockup notes:

- The page builder should feel controlled and premium, not like a blank website builder.

### 7.11 Content Studio

Purpose:

- Manage campaign-aware content across LinkedIn, email, WhatsApp, articles, newsletters, scripts, decks, and one-pagers.

Must include:

- Content cards/list.
- Campaign/channel/status filters.
- Generate content pack.
- Quality summary.
- CMO suggestions.
- Approval state.
- Revision state.

Mockup notes:

- Content should be operationally trackable, not just an editor screen.
- Quality score should guide attention.

### 7.12 Creative Production Desk

Purpose:

- Manage designer/editor production tasks.

Must include:

- Board/list toggle.
- Board columns: Briefed, In Progress, Uploaded, Revision, Approved.
- Owner, campaign, asset type, status, deadline filters.
- Selected task detail.
- Brief/files panel.
- Upload new version.
- Request changes.
- Approve.

Mockup notes:

- Board is default.
- List view is required for deadlines and bulk operations.

### 7.13 Reply Intelligence

Purpose:

- Show Outlook and WhatsApp replies that require classification, follow-up, or handoff.

Must include:

- Reply queue.
- Channel.
- Intent.
- Confidence.
- Lead score change.
- Suggested action.
- Assign owner.
- Mark handled.

Mockup notes:

- High-intent replies should visually rise to the top.
- Classification confidence should be visible.

### 7.14 Analytics

Purpose:

- Show what is working and what should change next.

Must include:

- CMO analytics summary.
- Leads added.
- Replies.
- Meetings.
- Landing page conversion rate.
- Campaign performance.
- Channel performance.
- Warm signals.
- Next recommendation.

Mockup notes:

- Analytics should be decision-oriented, not chart-heavy.
- Every chart should answer what to continue, pause, fix, or scale.

### 7.15 Admin / Integrations

Purpose:

- Monitor system health, integration status, users, audit logs, and spend.

Must include:

- Integration status table.
- OpenAI usage.
- Apollo credits.
- SendGrid webhooks.
- Microsoft Graph sync.
- WhatsApp API health.
- S3 uploads.
- Make webhooks if used.
- Spend dashboard entry.
- Users/roles.
- Audit log.
- Backup status.

Mockup notes:

- Spend should be visible here, not on general Today.
- Spend view should support provider, feature, agent, campaign, month, usage trend, alerts.

---

## 8. Clickable Prototype Flow

The first clickable prototype should demonstrate one complete growth loop.

Recommended scenario:

`Seasonal enterprise event campaign`

Prototype path:

1. Founder opens Today.
2. CMO Brain recommends focusing on a seasonal AGM/investor communication lane.
3. Founder opens Campaign Portfolio.
4. Campaign lane shows active status and blockers.
5. Founder opens Lead Detail for a hot lead.
6. Lead score, warm signals, and next-best action are visible.
7. Founder opens Landing Page Builder.
8. Landing page draft is edited and submitted for approval.
9. Founder opens Approvals and approves the landing page/content.
10. LinkedIn Operator opens their Today view and completes an assigned LinkedIn task.
11. Prospect reply appears in Reply Intelligence.
12. Reply is classified as meeting intent.
13. Sales task is created.
14. Friday Analytics shows campaign performance and next recommendation.

Prototype goal:

- Prove that the system can move from strategy to action to signal to follow-up to learning.

---

## 9. UI States Required In Mockups

For each major screen, include:

- Default data-filled state.
- Empty state.
- Loading state.
- Error state.
- Permission-restricted state where relevant.
- Approval pending state.
- Blocked/high-risk state where relevant.

Critical examples:

- Lead suppressed from outreach.
- Landing page proof asset requires permission.
- WhatsApp bot low confidence handoff.
- Agent run failed.
- SendGrid webhook warning.
- Apollo enrichment failed.
- Fourth campaign activation blocked by three-active-lane rule.

---

## 10. Design Handoff Requirements

High-fidelity mockups should include:

- Desktop layout first.
- Tablet-width adaptation for operators.
- Component inventory.
- Design tokens.
- Status chip mapping.
- Icons used.
- Button hierarchy.
- Table row behavior.
- Form states.
- Modal/drawer patterns.
- Approval flow states.
- Empty/loading/error states.
- Interaction notes.
- Prototype links between core screens.

Do not begin full frontend implementation until:

- Core command system mockups are approved.
- Component system is agreed.
- Prototype flow is tested with the founder/marketing owner.
- Engineering has screen-level data/API expectations.

---

## 11. Component Inventory For Design

Core components:

- App shell.
- Sidebar navigation.
- Top bar.
- Page header.
- Metric card.
- CMO recommendation panel.
- Approval card.
- Lead score badge.
- Status chip.
- Campaign lane card.
- Task card.
- Agent run row.
- Agent output preview.
- Timeline item.
- Warm signal item.
- Data table.
- Filter bar.
- Search input.
- Split queue/detail layout.
- Section editor.
- File upload block.
- Proof asset selector.
- Comment/revision thread.
- Board column.
- Creative task card.
- Modal.
- Drawer.
- Toast/notification.
- Empty state.
- Error state.

Recommended icon set:

- Lucide icons or similar.

Common icons:

- Search.
- Filter.
- Calendar.
- Clock.
- Check.
- X.
- Alert triangle.
- External link.
- Copy.
- Upload.
- Download.
- Edit.
- Refresh.
- Settings.
- User.
- Users.
- Mail.
- Message circle.
- Phone.
- File.
- Image.
- Video.
- Bar chart.
- Activity.
- Bot or sparkle for AI, used sparingly.

---

## 12. Screen Density Guidance

This product should support repeated daily work. Screens should be efficient.

Density rules:

- Use compact tables for data-heavy workflows.
- Use split panes for queues and selected detail.
- Use cards for campaign lanes, approvals, tasks, and recommendations.
- Avoid large blank empty areas on operational screens.
- Use clear row spacing so tables remain readable.
- Keep primary action always visible near the relevant context.

Best pattern by module:

| Module | Recommended Layout |
| --- | --- |
| Today | Metric cards + campaign lane cards + queues |
| Approvals | Split queue/detail |
| Leads | Table + right-side preview or detail page |
| Lead Detail | Detail + timeline + right decision panel |
| Campaign Portfolio | Lane cards + blockers + draft list |
| LinkedIn Workbench | Split task queue/detail |
| Landing Page Builder | Section list + editor + preview |
| Content Studio | Filtered cards/list + quality summary |
| Creative Desk | Board + list toggle |
| Reply Intelligence | Split reply queue/detail |
| Agent Ops | Agent table + selected run detail |
| Analytics | Summary panels + focused charts |
| Admin | Integration table + spend dashboard + audit list |

---

## 13. Content And Copy Rules

UI copy should be:

- Direct.
- Operational.
- Specific.
- Decision-oriented.
- Low drama.

Use:

- "Needs approval"
- "Blocked by proof asset"
- "Meeting intent detected"
- "Create follow-up task"
- "Suppressed from outreach"
- "Recommended because..."

Avoid:

- "Unlock your growth potential"
- "Supercharge your sales"
- "AI magic"
- "Revolutionary"
- Generic motivational copy.

CMO recommendation copy should always include:

- What to do.
- Why it matters.
- What evidence supports it.
- What risk exists.
- What action is required.

---

## 14. Mockup Deliverables

Recommended deliverables:

1. UI direction board.
2. Design tokens page.
3. Component library page.
4. Phase 1 high-fidelity mockups.
5. Phase 2 high-fidelity mockups.
6. Clickable prototype.
7. UI state sheet.
8. Engineering handoff notes.

Minimum first batch:

- Today / Command Centre.
- Approvals.
- Campaign Portfolio.
- Lead Detail.
- CMO Brain.
- Agent Ops.
- Component tokens and status chips.

---

## 15. Resolved UI Decisions

### 15.1 Primary Font

Decision: Use `Inter` as the primary UI font.

Fallback stack:

```css
font-family: Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
```

Reason:

- Inter is highly legible for dense SaaS interfaces.
- It handles tables, numbers, forms, and compact labels well.
- It feels operational and premium without becoming decorative.

Implementation notes:

- Use tabular numerals for metric cards, tables, and dashboards.
- Use font weight `500` for labels and table headers.
- Use font weight `600` for panel titles and important action headings.
- Avoid heavy `700+` usage except rare page-level emphasis.

### 15.2 Zlicc Primary Accent

Decision: Use `#00A8C8` as the primary Zlicc cyan for the Growth Console UI.

Supporting tokens:

| Token | Hex | Usage |
| --- | --- | --- |
| `zlicc-cyan-600` | `#00A8C8` | Primary accent, selected nav, primary links, active indicators |
| `zlicc-cyan-700` | `#0089A3` | Hover/pressed state |
| `zlicc-cyan-50` | `#E9FAFD` | Soft accent background |
| `zlicc-cyan-100` | `#CFF3F8` | Selected row or subtle highlight |

Rules:

- Use cyan to guide attention, not to decorate entire screens.
- Primary action buttons may use cyan when the action is safe and central.
- Risk, pending, success, and blocked states must use semantic colors, not cyan.

### 15.3 Sidebar Width

Decision:

- Expanded sidebar: `264px`.
- Collapsed sidebar: `72px`.
- Sidebar internal padding: `16px`.
- Navigation item height: `40px`.

Reason:

- `264px` gives enough room for grouped navigation labels without wrapping.
- `72px` collapsed mode keeps icon navigation usable on smaller screens.
- Stable sidebar width prevents layout shifts between modules.

Behavior:

- Founder/Admin default: expanded.
- Operator tablet view: collapsed or compact by default.
- Sidebar should remember the user's last state.

### 15.4 Right-Side Drawers

Decision: Use right-side drawers for quick detail views.

Drawer usage:

- Lead quick preview from lead list.
- Approval detail from approval queue.
- Task detail from Today.
- Agent run output from Agent Ops.
- Asset/proof preview from Asset Library.
- Reply detail from Reply Intelligence.

Drawer sizes:

- Standard drawer: `480px`.
- Wide drawer: `640px` for content previews, landing page snippets, reply threads, and agent outputs.

Rules:

- Drawers are for inspection and quick actions.
- Full editing flows still open full pages when the workflow is complex.
- Drawers should not stack more than one level deep in V1.

### 15.5 Today Layout

Decision: Use a 12-column dashboard grid with a fixed hierarchy.

Reason:

- The Today screen must adapt by role without creating separate page designs for every user.
- A 12-column grid gives design flexibility while preserving order.
- Fixed hierarchy keeps the screen operational rather than becoming a free-form dashboard builder.

Founder layout:

- CMO Priority: 12 columns.
- Hot Replies, Approvals, WA Handoffs, Tasks: 3 columns each.
- Active Campaign Lanes: 8 columns.
- Work Queues: 4 columns.
- Hot Leads: 8 columns.
- Weekly Learning: 4 columns.

Operator layout:

- Assigned Queue: 8 columns.
- Due/Overdue Summary: 4 columns.
- Selected Task/Copy Preview: 12 columns or split 7/5.

Rules:

- Users do not customize the grid in V1.
- Role determines the layout.
- Future V2 can allow configurable widgets if needed.

### 15.6 Creative Calendar View

Decision: Do not ship Creative Calendar View in V1.

V1 will include:

- Kanban board view.
- Table/list view.
- Deadline filters.
- Overdue indicators.
- Owner and campaign filters.

Reason:

- Board and list cover the immediate operational need.
- Calendar view adds complexity and can wait until creative task volume proves the need.

V1.1/V2 candidate:

- Calendar view for production deadlines.
- Workload view by owner.
- Capacity heatmap.

### 15.7 Chart Style

Decision: Use restrained operational charts, not decorative dashboard visuals.

Chart style:

- Simple line charts for trends.
- Bar charts for source/channel comparison.
- Funnel or stage conversion view for lead movement.
- Small KPI cards for top-line metrics.
- Minimal donut charts; use only when comparing a few stable categories.

Visual rules:

- White panel background.
- Thin grid lines in `slate-200`.
- Axis labels in `slate-500`.
- Primary series in `zlicc-cyan-600`.
- Secondary series in slate, green, amber, or red based on meaning.
- Avoid gradients, 3D charts, oversized chart titles, and chart-heavy screens.

Analytics principle:

> Every chart must answer what to continue, pause, fix, or scale.

### 15.8 Mobile And Tablet Expectations

Decision: V1 is desktop-first, tablet-supported, and mobile-limited.

Desktop:

- Full experience.
- Best for founder, admin, campaign planning, content, analytics, and page builder.

Tablet:

- Supported for operators and reviewers.
- LinkedIn Operator, Creative Task review, Approvals, Tasks, and Reply triage should be usable.
- Sidebar may collapse by default.
- Tables can switch to stacked row cards where needed.

Mobile:

- Not a full V1 working surface.
- Support only quick actions where practical:
  - View Today summary.
  - Approve/reject simple items.
  - View hot reply.
  - Mark task done.
  - Add quick capture note.

Minimum responsive expectations:

- Desktop design target: `1440px`.
- Tablet target: `1024px`.
- Mobile quick-action target: `390px`.

Rules:

- Landing Page Builder, Content Studio, Campaign Portfolio, Analytics, and Admin are desktop-first.
- LinkedIn Operator and Creative Team views must be comfortable on tablet.
- Mobile should not block core business, but it is not the primary production interface in V1.
