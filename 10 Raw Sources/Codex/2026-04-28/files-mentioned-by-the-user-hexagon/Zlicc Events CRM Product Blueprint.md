# Zlicc Events CRM Product Blueprint

## 1. Product Positioning

Zlicc Events CRM is a multi-tenant operating system for event agencies. It manages the full commercial and delivery lifecycle from company and contact creation through leads, pitches, projects, SOP checklists, feedback, and leadership reporting.

The product is owned and branded as a Zlicc platform. Each onboarded organisation, such as Hexagon, can upload its own logo to create a co-branded experience inside the Zlicc shell.

### Brand Experience

- Zlicc remains the primary product identity.
- Tenant logos appear in the workspace header, organisation switcher, exported reports, and client-facing feedback pages.
- The UI follows Zlicc's premium SaaS system: black, white, cloud neutrals, luminous cyan for primary actions, and yellow only for premium or high-value emphasis.
- The product should feel operational, calm, data-rich, and fast, not like a marketing landing page.

## 2. Multi-Tenant Hierarchy

```text
Zlicc Platform
  -> Organisation / Tenant
    -> Users & Roles
    -> Companies
      -> Contacts
      -> Leads
        -> Sales DSR / Activities
        -> Pitches
          -> Projects
            -> Project Tasks
            -> SOP Checklists
            -> Pre-Event PFS
            -> Post-Event Actuals
            -> Client Feedback
            -> Internal Feedback
```

### Tenant-Level Settings

Each organisation should support:

- Organisation name
- Uploaded client logo
- Workspace theme preview within Zlicc brand constraints
- Users
- Role assignments
- Module access settings
- Feedback form branding
- Import templates
- Email/WhatsApp integration settings, to be activated later

## 3. Roles And Access

### Admin

Full access to all tenant modules, settings, users, permissions, dashboards, financials, projects, feedback, imports, exports, and templates.

### Leadership

Full operational and reporting access, excluding admin-only configuration such as user management and tenant settings unless explicitly granted.

### Sales

Sales should access:

- Companies and contacts needed for lead work
- Leads funnel
- Pitch funnel
- Sales DSR
- Follow-ups
- Calendar reminders
- Sales dashboard
- Relevant client feedback visibility

Sales should not access:

- Detailed project financial profitability
- Admin panel
- Global permission settings
- Internal project delivery controls unless assigned or granted

### Client Servicing

Client Servicing should access:

- Pitch funnel
- Projects funnel
- Assigned project details
- Project task coordination
- SOP checklists
- Client feedback
- Internal feedback
- Client servicing dashboard

Client Servicing should not access:

- Admin panel
- Tenant-wide financial profitability unless granted

### Operations

Operations should access:

- Assigned project details
- Execution tasks
- SOP checklists
- Event readiness status
- Issue logs
- Vendor/manual cost inputs where relevant
- Operations dashboard
- Internal feedback

Operations should not access:

- Admin panel
- Sales-only DSR views unless linked to an assigned project
- Tenant-wide financial profitability unless granted

## 4. Core Data Objects

### Organisation

Represents a tenant onboarded into Zlicc.

Key fields:

- Organisation name
- Logo
- Industry
- Admin users
- Active modules
- Integration status
- Created date
- Subscription/status

### Company

Represents a client or prospect organisation.

Key fields:

- Company name
- Industry/category
- Website
- Address/city
- Relationship owner
- Notes
- Status: Prospect, Active Client, Dormant, Archived

### Contact

Contacts are created under a company. One company may have multiple contacts.

Key fields:

- Full name
- Designation
- Email
- Phone
- WhatsApp number
- Decision-maker flag
- Department/function
- Relationship notes
- Linked company

### Lead

Every lead must be linked to a company and one or more contacts.

Key fields:

- Lead title
- Company
- Contacts
- Lead owner
- Lead source
- Lead temperature: Hot, Potential, Cold, Non-responsive
- Brief received: Yes/No
- Date contacted
- Next follow-up date
- Lead status
- Notes
- Communication snapshot

### Sales DSR / Activity

Daily sales activity attached to a lead.

Activity types:

- Call
- Meeting
- Follow-up
- Email
- WhatsApp
- Note
- Reminder
- Calendar event

Key fields:

- Activity type
- Activity owner
- Date/time
- Outcome
- Next action
- Next action date
- Attachment/reference
- Linked lead

### Pitch

Created when a lead receives a brief or scope of work and moves into pitch management.

Pitch stages:

- Enquiry Stage
- Brief Stage
- Proposal Stage
- Won
- Lost
- Cold
- Cancelled

Key fields:

- Pitch title
- Source lead
- Company
- Contacts
- Pitch owner
- Stage
- Expected value
- Expected event date
- Scope summary
- Comments
- Follow-up date
- Win/loss reason

### Project

Created when a pitch is marked Won.

Key fields:

- Project name
- Linked pitch
- Company
- Contacts
- Event date
- Venue
- Event scope
- Project status: Planning, Live, Completed, Cancelled
- Client servicing owner
- Operations owner
- Assigned team
- Feedback URL

### Vendor Entries

Vendors are not a master database in the first version. Vendor data is manually entered within project financial and operational workflows.

Key fields:

- Vendor name
- Service category
- Contact person
- Phone/email
- Estimated cost
- Actual cost
- Payment status
- Notes

## 5. Module Specification

## 5.1 Company And Contacts

Purpose: Create a structured CRM base before leads are created.

Required features:

- Company creation
- Multiple contacts under company
- Contact tagging to leads and pitches
- Search and filters
- Company timeline showing leads, pitches, projects, feedback, and revenue history
- Import template for companies and contacts

## 5.2 Leads Funnel

Purpose: Manage lead capture, qualification, follow-up, and sales activity.

Required features:

- Create lead against company and contacts
- Lead temperature filters
- Brief received filter
- Date contacted and next follow-up
- Daily reminders
- Sales DSR timeline
- Calendar event trigger
- Week, month, quarter, and year summaries
- Lead conversion to pitch
- Import template for historical leads

Recommended views:

- Table view
- Kanban by temperature/status
- Follow-ups due
- Overdue follow-ups
- My leads

## 5.3 Pitch Funnel

Purpose: Manage briefs, proposals, and commercial conversion.

Required features:

- Pitch creation from lead
- Stage tracking
- Follow-up tracking
- Proposal status
- Comments
- Won/lost/cancelled handling
- Conversion to project when marked Won
- Week, month, quarter, and year summaries

Recommended views:

- Pipeline board by stage
- Table view
- Follow-ups due
- Won/lost analysis

## 5.4 Projects Funnel

Purpose: Manage events after commercial closure.

Required features:

- Auto-create project from Won pitch
- Project home page
- Active/completed project list
- Assignment-based access
- Event details
- Client details
- Scope, venue, date, and status
- Pre-event PFS
- Project tasks and timeline
- Manual vendor entries
- SOP checklist generated from global templates
- Post-event actuals
- Client feedback
- Internal feedback

Recommended project tabs:

- Overview
- Tasks
- Pre-Event PFS
- SOP Checklist
- Execution Notes
- Post-Event Actuals
- Feedback
- Internal Review

## 5.5 SOP And Quality Control

Purpose: Standardise quality, safety, compliance, and readiness across projects.

Global SOP template categories:

- Safety checklist
- Required permissions
- Specific add-on elements
- Crowd control
- Emergency readiness
- Incident reporting

Project-specific behavior:

- A project checklist is generated from selected SOP templates.
- Items can be assigned to Client Servicing or Operations.
- Checklist items carry due date, owner, status, and comments.
- Admin/Leadership can view compliance across all projects.

## 5.6 Feedback System

Purpose: Collect client and internal feedback after event completion.

Client feedback:

- Unique feedback URL per project
- Custom fields per event/project
- Overall rating 1-5
- Planning feedback
- Execution feedback
- Communication feedback
- Improvement suggestions
- Testimonial capture
- Send request via WhatsApp or email when integrations are active

Internal feedback:

- Issues faced
- Budget deviation reasons
- Vendor performance
- Client handling insights
- Operational learnings

## 5.7 Finance And Profitability

Purpose: Track project and business-level financial performance.

Access:

- Admin and Leadership by default
- Other roles only if granted

Project-level fields:

- Client name
- Project name
- Revenue / billing value
- Internal cost
- Vendor cost breakdown through manual entries or attachment
- Profit
- Profit percentage
- Budget vs actual

Business-level insights:

- Monthly revenue
- Quarterly revenue
- Yearly revenue
- Client-wise revenue
- Client-wise profitability
- Average margin
- Total revenue
- Total profit

## 6. Dashboards

## 6.1 Admin And Leadership Dashboard

Purpose: Holistic command center.

Widgets:

- Total leads
- Conversion rate
- Pitch pipeline
- Won/lost trends
- Active projects
- Upcoming events
- Revenue vs cost
- Profit percentage
- Follow-ups due
- SOP compliance
- Feedback ratings
- Team workload
- Client-wise performance
- Project risk alerts

## 6.2 Sales Dashboard

Purpose: Action-first daily sales cockpit.

Widgets:

- My leads
- Hot leads
- Follow-ups due today
- Overdue follow-ups
- Recent DSR activity
- Pitches awaiting action
- Calendar reminders
- Lead-to-pitch conversion
- Pitch-to-win conversion

## 6.3 Client Servicing Dashboard

Purpose: Client and delivery coordination.

Widgets:

- Assigned active projects
- Upcoming events
- Pending client actions
- Project task status
- SOP checklist progress
- Feedback pending
- Internal review pending
- Client communication reminders

## 6.4 Operations Dashboard

Purpose: Event execution and readiness.

Widgets:

- Assigned projects
- Upcoming live events
- Pending operational tasks
- SOP readiness
- Incident logs
- Vendor/manual entry tasks
- Execution notes
- Post-event actuals pending

## 7. Import Templates

The CRM should not simply mirror existing Excel sheets. Zlicc should define clean import templates aligned with the redesigned data model.

Initial templates:

- Companies import
- Contacts import
- Leads import
- Pitch import
- Projects import
- Finance/PFS import

Each import should include:

- Required field validation
- Duplicate detection
- Preview before import
- Error report
- Sample downloadable template

## 8. Integrations

### Phase 1

No live WhatsApp or email integration required.

### Future Integration Readiness

The system should be architected to support:

- Zlicc-owned WhatsApp service
- SendGrid email provider
- Feedback request sending
- Campaign communication
- Response tracking
- Calendar events

## 9. Zlicc UI/UX Direction

### Product Shell

- Left sidebar with module navigation
- Top workspace bar with Zlicc identity and tenant logo
- Organisation switcher for multi-tenant users
- Role-aware navigation
- Compact data tables
- Pipeline boards
- Dashboard metric strips
- Dark glossy command surfaces for leadership dashboards
- Light cloud operational surfaces for daily work

### Core UI Components

- Tenant switcher
- Role-aware sidebar
- Company/contact drawer
- Lead detail panel
- Activity timeline
- Pitch pipeline board
- Project command page
- SOP checklist table
- Feedback form builder
- Finance summary cards
- Import wizard
- Permission matrix

### Visual Treatment

- Cyan primary CTAs and focus states
- Yellow only for premium, high-value, or critical business highlights
- White/cloud page background for operational modules
- Graphite dark panels for executive command areas
- Hairline borders, soft shadows, and restrained glossy highlights
- Dense but readable tables and dashboards

## 10. Recommended Build Phases

Although the long-term product is the full CRM, the build can be sequenced in delivery phases.

### Phase 1: CRM Foundation

- Multi-tenant organisation setup
- Client logo upload
- User roles
- Companies
- Contacts
- Leads
- Sales DSR
- Lead follow-ups and calendar reminders

### Phase 2: Pitch And Project Conversion

- Pitch funnel
- Pitch stages
- Won-to-project conversion
- Project list and project home
- Assignment-based project access

### Phase 3: Project Delivery

- Tasks
- Manual vendor entries
- Pre-event PFS
- SOP templates
- Project-specific checklists
- Operations dashboard
- Client servicing dashboard

### Phase 4: Feedback And Finance

- Unique feedback URL
- Custom feedback fields
- Client feedback dashboard
- Internal feedback
- Post-event actuals
- Profitability dashboard

### Phase 5: Integrations And Campaigns

- WhatsApp service integration
- SendGrid integration
- Feedback sending
- Campaigns
- Response tracking

## 11. Open Product Decisions

These can be decided during design or implementation:

- Whether users can belong to multiple tenants.
- Whether feedback URLs should be public, token-protected, or OTP-protected.
- Whether project access is granted by assignment only or by module-wide role access.
- Whether calendar reminders sync with Google/Microsoft calendars or remain internal first.
- Whether finance imports should support attachments only or structured row-level import.

