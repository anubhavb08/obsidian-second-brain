# Zlicc Events CRM Database Schema

Recommended database: PostgreSQL 15+ on AWS RDS or Aurora PostgreSQL.

All tenant-owned business tables should include `tenant_id`, `created_at`, `updated_at`, and optionally `deleted_at` for soft deletion. Use UUID primary keys in production.

## Core Tenancy

### tenants

Stores each onboarded organisation such as Hexagon or Lumina.

| Column | Type | Notes |
| --- | --- | --- |
| id | uuid pk | Tenant id |
| name | varchar(180) | Organisation name |
| slug | varchar(80) unique | URL/workspace slug |
| plan | varchar(40) | Growth, Enterprise, Custom |
| logo_url | text | Client uploaded logo |
| mark | varchar(8) | Short workspace mark |
| license_limit | integer | Purchased licences |
| active_users | integer | Cached count or derived |
| status | varchar(40) | Active, Suspended, Trial |
| join_link | text | Tenant admin/user invite link |
| created_at | timestamptz |  |
| updated_at | timestamptz |  |

Indexes: `slug`, `status`.

### users

Stores Zlicc super admins and tenant users.

| Column | Type | Notes |
| --- | --- | --- |
| id | uuid pk | User id |
| tenant_id | uuid fk nullable | Null or Zlicc tenant for super admins |
| role | varchar(40) | super-admin, admin, leadership, sales, client-servicing, operations |
| full_name | varchar(180) |  |
| email | citext unique | Login email |
| mobile | varchar(32) |  |
| password_hash | text | If not using Cognito/Auth0 |
| status | varchar(40) | Invited, Active, Suspended |
| last_login_at | timestamptz |  |
| created_at | timestamptz |  |
| updated_at | timestamptz |  |

Indexes: `(tenant_id, role)`, `email`, `(tenant_id, status)`.

### tenant_modules

Controls which modules a tenant can access.

| Column | Type | Notes |
| --- | --- | --- |
| id | uuid pk |  |
| tenant_id | uuid fk |  |
| module_key | varchar(80) | companies, contacts, leads, pitches, projects, sops, feedback, finance |
| enabled | boolean |  |
| created_at | timestamptz |  |

Unique: `(tenant_id, module_key)`.

## CRM Master Data

### companies

| Column | Type | Notes |
| --- | --- | --- |
| id | uuid pk |  |
| tenant_id | uuid fk |  |
| name | varchar(220) |  |
| industry | varchar(120) | Stored at company level and inherited by leads |
| owner_user_id | uuid fk users | Account owner |
| status | varchar(60) | Prospect, Active Client, Dormant |
| city | varchar(120) |  |
| notes | text |  |
| created_at | timestamptz |  |
| updated_at | timestamptz |  |
| deleted_at | timestamptz nullable |  |

Indexes: `(tenant_id, name)`, `(tenant_id, industry)`, `(tenant_id, owner_user_id)`.

### contacts

| Column | Type | Notes |
| --- | --- | --- |
| id | uuid pk |  |
| tenant_id | uuid fk | Denormalised for fast tenancy checks |
| company_id | uuid fk companies |  |
| name | varchar(180) |  |
| designation | varchar(180) |  |
| email | citext |  |
| phone | varchar(32) |  |
| decision_maker | boolean |  |
| notes | text |  |
| created_at | timestamptz |  |
| updated_at | timestamptz |  |
| deleted_at | timestamptz nullable |  |

Indexes: `(tenant_id, company_id)`, `(tenant_id, email)`, `(tenant_id, phone)`.

## Sales Flow

### leads

| Column | Type | Notes |
| --- | --- | --- |
| id | uuid pk |  |
| tenant_id | uuid fk |  |
| company_id | uuid fk companies |  |
| title | varchar(240) | Lead/event title |
| owner_user_id | uuid fk users | Sales owner |
| source | varchar(120) | Referral, Website, Outbound, etc. |
| industry | varchar(120) | Defaults from company, editable |
| temperature | varchar(40) | Hot, Warm, Potential, Cold |
| stage | varchar(80) | In Touch, Brief Received, Cold, Not Responding |
| tag | varchar(40) | Low, Medium, High |
| brief_received | boolean |  |
| status | varchar(120) | Current sales status |
| date_contacted | date |  |
| next_follow_up | date |  |
| value | numeric(14,2) | Estimated lead value |
| created_at | timestamptz |  |
| updated_at | timestamptz |  |
| deleted_at | timestamptz nullable |  |

Indexes: `(tenant_id, owner_user_id)`, `(tenant_id, stage)`, `(tenant_id, next_follow_up)`.

### lead_contacts

Many-to-many mapping between leads and contacts.

| Column | Type | Notes |
| --- | --- | --- |
| lead_id | uuid fk leads |  |
| contact_id | uuid fk contacts |  |
| is_primary | boolean |  |

Primary key: `(lead_id, contact_id)`.

### lead_activities

Daily sales report / touchpoint records.

| Column | Type | Notes |
| --- | --- | --- |
| id | uuid pk |  |
| tenant_id | uuid fk |  |
| lead_id | uuid fk leads |  |
| type | varchar(40) | Call, Meeting, Email, Message |
| owner_user_id | uuid fk users |  |
| activity_date | date |  |
| activity_time | time |  |
| outcome | text |  |
| next_action | text |  |
| next_follow_up | date |  |
| status | varchar(40) | Open, Completed |
| created_at | timestamptz |  |
| updated_at | timestamptz |  |

Indexes: `(tenant_id, lead_id)`, `(tenant_id, owner_user_id, activity_date)`.

### meetings

Dedicated meeting records when imported or scheduled.

| Column | Type | Notes |
| --- | --- | --- |
| id | uuid pk |  |
| tenant_id | uuid fk |  |
| lead_id | uuid fk leads nullable |  |
| company_id | uuid fk companies |  |
| contact_id | uuid fk contacts nullable |  |
| meeting_date | date |  |
| meeting_time | time |  |
| address | text |  |
| location | varchar(160) |  |
| stage | varchar(80) |  |
| tag | varchar(40) |  |
| follow_up | date |  |
| created_at | timestamptz |  |
| updated_at | timestamptz |  |

Indexes: `(tenant_id, meeting_date)`, `(tenant_id, company_id)`.

## Pitch Funnel

### pitches

| Column | Type | Notes |
| --- | --- | --- |
| id | uuid pk |  |
| tenant_id | uuid fk |  |
| lead_id | uuid fk leads nullable |  |
| company_id | uuid fk companies |  |
| title | varchar(240) |  |
| owner_user_id | uuid fk users |  |
| stage | varchar(60) | Brief, Proposal, Won, Lost, Cold, Cancelled, Postponed |
| expected_value | numeric(14,2) | Pitch projection |
| creation_date | date |  |
| event_date | date |  |
| follow_up | date |  |
| comments | text |  |
| created_at | timestamptz |  |
| updated_at | timestamptz |  |
| deleted_at | timestamptz nullable |  |

Indexes: `(tenant_id, stage)`, `(tenant_id, owner_user_id)`, `(tenant_id, event_date)`.

## Projects And Operations

### projects

| Column | Type | Notes |
| --- | --- | --- |
| id | uuid pk |  |
| tenant_id | uuid fk |  |
| pitch_id | uuid fk pitches nullable |  |
| company_id | uuid fk companies |  |
| name | varchar(240) |  |
| venue | varchar(240) |  |
| event_date | date |  |
| status | varchar(60) | Planning, Live, Completed, Cancelled |
| cs_owner_user_id | uuid fk users | Client servicing owner |
| ops_owner_user_id | uuid fk users | Operations owner |
| logistics_lead_user_id | uuid fk users nullable |  |
| estimate_value | numeric(14,2) | Manual estimate |
| revenue | numeric(14,2) | Closed/won project revenue |
| internal_cost | numeric(14,2) | Fallback cost |
| vendor_cost | numeric(14,2) | Fallback vendor cost |
| sop_progress | integer | Cached readiness percent |
| scope | text |  |
| feedback_url | text | Unique customer feedback link |
| created_at | timestamptz |  |
| updated_at | timestamptz |  |
| deleted_at | timestamptz nullable |  |

Indexes: `(tenant_id, status)`, `(tenant_id, event_date)`, `(tenant_id, company_id)`.

### project_line_items

Used for PFS, actuals, finance, tasks, SOP notes, and feedback notes.

| Column | Type | Notes |
| --- | --- | --- |
| id | uuid pk |  |
| project_id | uuid fk projects |  |
| section | varchar(80) | Pre-Event PFS, Post-Event Actuals, Finance, Tasks, SOP Checklist, Client Feedback, Internal Feedback |
| category | varchar(140) |  |
| vendor | varchar(180) | Manual vendor entry |
| owner | varchar(180) | Optional owner |
| description | text |  |
| estimated | numeric(14,2) |  |
| actual | numeric(14,2) |  |
| status | varchar(60) | Estimated, Approved, Actual, Open |
| created_at | timestamptz |  |
| updated_at | timestamptz |  |

Indexes: `(project_id, section)`, `(project_id, status)`.

### project_tasks

If tasks are separated from line items in production.

| Column | Type | Notes |
| --- | --- | --- |
| id | uuid pk |  |
| tenant_id | uuid fk |  |
| project_id | uuid fk projects |  |
| title | varchar(240) |  |
| owner_role | varchar(80) | Operations, Client Servicing |
| owner_user_id | uuid fk users nullable |  |
| due_date | date |  |
| status | varchar(60) | Open, In progress, Blocked, Completed |
| created_at | timestamptz |  |
| updated_at | timestamptz |  |

Indexes: `(tenant_id, owner_user_id, due_date)`, `(project_id, status)`.

## SOPs

### sop_templates

Global reusable SOP templates per tenant.

| Column | Type | Notes |
| --- | --- | --- |
| id | uuid pk |  |
| tenant_id | uuid fk nullable | Null for Zlicc global templates |
| name | varchar(220) |  |
| code | varchar(80) |  |
| category | varchar(120) | Safety, Compliance, Execution |
| phase | varchar(120) | Pre-event, Live, Post-event |
| version | varchar(40) |  |
| risk_level | varchar(60) | Standard, High |
| owner_role | varchar(120) |  |
| approver_role | varchar(120) |  |
| review_cadence | varchar(120) |  |
| escalation_sla | varchar(120) |  |
| objective | text |  |
| applicability | text |  |
| triggers | text |  |
| acceptance_criteria | text |  |
| failure_response | text |  |
| compliance_notes | text |  |
| created_at | timestamptz |  |
| updated_at | timestamptz |  |

Indexes: `(tenant_id, category)`, `(tenant_id, code)`.

### sop_template_items

| Column | Type | Notes |
| --- | --- | --- |
| id | uuid pk |  |
| template_id | uuid fk sop_templates |  |
| sort_order | integer |  |
| item_text | text |  |
| evidence_required | boolean |  |
| required | boolean |  |

Index: `(template_id, sort_order)`.

### sop_template_evidence

| Column | Type | Notes |
| --- | --- | --- |
| id | uuid pk |  |
| template_id | uuid fk sop_templates |  |
| evidence_name | varchar(180) | Photo proof, NOC, signed checklist |

### project_sops

SOP templates assigned to a project.

| Column | Type | Notes |
| --- | --- | --- |
| id | uuid pk |  |
| project_id | uuid fk projects |  |
| template_id | uuid fk sop_templates |  |
| name | varchar(220) | Project-level copy |
| category | varchar(120) |  |
| total_items | integer |  |
| completed_items | integer |  |
| owner_user_id | uuid fk users nullable |  |
| due_date | date |  |
| status | varchar(60) | Open, In progress, Completed, Blocked |
| notes | text |  |
| created_at | timestamptz |  |
| updated_at | timestamptz |  |

Unique: `(project_id, template_id)`.

### project_sop_items

Project-specific checklist compliance.

| Column | Type | Notes |
| --- | --- | --- |
| id | uuid pk |  |
| project_sop_id | uuid fk project_sops |  |
| item_text | text |  |
| completed | boolean |  |
| accepted | boolean |  |
| proof_attachment_id | uuid fk attachments nullable |  |
| proof_notes | text |  |
| completed_by_user_id | uuid fk users nullable |  |
| completed_at | timestamptz nullable |  |

Index: `(project_sop_id, completed, accepted)`.

## Feedback

### feedback_templates

| Column | Type | Notes |
| --- | --- | --- |
| id | uuid pk |  |
| tenant_id | uuid fk |  |
| name | varchar(220) |  |
| type | varchar(40) | Client, Internal |
| owner_role | varchar(120) |  |
| objective | text |  |
| created_at | timestamptz |  |
| updated_at | timestamptz |  |

Indexes: `(tenant_id, type)`.

### feedback_template_fields

| Column | Type | Notes |
| --- | --- | --- |
| id | uuid pk |  |
| template_id | uuid fk feedback_templates |  |
| sort_order | integer |  |
| label | text |  |
| field_type | varchar(60) | Rating, Short answer, Long answer, Select, Checkbox |
| required | boolean |  |
| options_json | jsonb | For select/rating scales |

Index: `(template_id, sort_order)`.

### feedback_template_checkboxes

| Column | Type | Notes |
| --- | --- | --- |
| id | uuid pk |  |
| template_id | uuid fk feedback_templates |  |
| sort_order | integer |  |
| label | text |  |

### project_feedback_forms

Client/internal forms attached to a project.

| Column | Type | Notes |
| --- | --- | --- |
| id | uuid pk |  |
| tenant_id | uuid fk |  |
| project_id | uuid fk projects |  |
| type | varchar(40) | Client, Internal |
| template_id | uuid fk feedback_templates nullable |  |
| owner_user_id | uuid fk users nullable |  |
| public_token | varchar(160) unique | Customer feedback URL token |
| status | varchar(60) | Draft form, Ready to send, Sent, Submitted, Closed |
| channel | varchar(60) | Email, WhatsApp, Internal review |
| rating | numeric(3,2) nullable |  |
| submitted_at | timestamptz nullable |  |
| created_at | timestamptz |  |
| updated_at | timestamptz |  |

Indexes: `(tenant_id, project_id, type)`, `public_token`, `(tenant_id, status)`.

### project_feedback_fields

Project-customised fields.

| Column | Type | Notes |
| --- | --- | --- |
| id | uuid pk |  |
| form_id | uuid fk project_feedback_forms |  |
| sort_order | integer |  |
| label | text |  |
| field_type | varchar(60) |  |
| required | boolean |  |
| options_json | jsonb |  |

### project_feedback_checkboxes

Project-customised checkbox controls.

| Column | Type | Notes |
| --- | --- | --- |
| id | uuid pk |  |
| form_id | uuid fk project_feedback_forms |  |
| sort_order | integer |  |
| label | text |  |

### feedback_responses

| Column | Type | Notes |
| --- | --- | --- |
| id | uuid pk |  |
| form_id | uuid fk project_feedback_forms |  |
| submitted_by_name | varchar(180) | Optional customer name |
| submitted_by_email | citext | Optional |
| rating | numeric(3,2) nullable |  |
| response_json | jsonb | Field answers and checkbox states |
| ip_address | inet nullable |  |
| user_agent | text nullable |  |
| submitted_at | timestamptz |  |

Index: `(form_id, submitted_at)`.

## Files, Imports, And Audit

### attachments

| Column | Type | Notes |
| --- | --- | --- |
| id | uuid pk |  |
| tenant_id | uuid fk |  |
| project_id | uuid fk projects nullable |  |
| uploaded_by_user_id | uuid fk users nullable |  |
| file_name | varchar(260) |  |
| mime_type | varchar(120) |  |
| file_size | bigint |  |
| s3_bucket | varchar(180) |  |
| s3_key | text |  |
| visibility | varchar(40) | private, tenant, public-token |
| created_at | timestamptz |  |

Indexes: `(tenant_id, project_id)`, `(tenant_id, uploaded_by_user_id)`.

### import_jobs

| Column | Type | Notes |
| --- | --- | --- |
| id | uuid pk |  |
| tenant_id | uuid fk |  |
| module_key | varchar(80) | companies, contacts, leads, meetings, etc. |
| uploaded_by_user_id | uuid fk users |  |
| attachment_id | uuid fk attachments nullable |  |
| status | varchar(60) | Uploaded, Previewed, Imported, Failed |
| rows_total | integer |  |
| rows_success | integer |  |
| rows_failed | integer |  |
| error_report_json | jsonb |  |
| created_at | timestamptz |  |
| updated_at | timestamptz |  |

Index: `(tenant_id, module_key, created_at)`.

### audit_logs

| Column | Type | Notes |
| --- | --- | --- |
| id | uuid pk |  |
| tenant_id | uuid fk nullable |  |
| actor_user_id | uuid fk users nullable |  |
| action | varchar(120) | create, update, delete, login, send_feedback |
| entity_type | varchar(120) | leads, projects, project_sops, etc. |
| entity_id | uuid nullable |  |
| before_json | jsonb nullable |  |
| after_json | jsonb nullable |  |
| ip_address | inet nullable |  |
| created_at | timestamptz |  |

Indexes: `(tenant_id, entity_type, entity_id)`, `(actor_user_id, created_at)`.

## Multi-Tenant Access Rules

- Zlicc Super Admin can manage tenants and tenant admin accounts, but should not browse tenant operational records by default.
- Tenant Admin and Leadership can view full tenant data.
- Sales users should only see leads, pitches, touchpoints, and reminders owned by them unless explicitly granted team visibility.
- Client Servicing and Operations users should see assigned projects, tasks, SOPs, feedback, and project records.
- All API queries must filter by `tenant_id` except Zlicc platform admin screens.

## Suggested API Modules

- `/auth`
- `/tenants`
- `/users`
- `/companies`
- `/contacts`
- `/leads`
- `/activities`
- `/meetings`
- `/pitches`
- `/projects`
- `/sop-templates`
- `/project-sops`
- `/feedback-templates`
- `/project-feedback`
- `/finance`
- `/imports`
- `/attachments`
- `/audit-logs`
