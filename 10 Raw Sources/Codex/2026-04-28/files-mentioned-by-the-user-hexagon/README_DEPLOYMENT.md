# Zlicc Events CRM Deployment Notes

## Current Package

This package is now structured as a full-stack PostgreSQL-backed CRM application with a PWA-capable front end.

- Front end: HTML, CSS, vanilla JavaScript
- Backend: Node.js + Express
- Database: PostgreSQL
- PostgreSQL driver: `pg`
- PWA: `manifest.webmanifest` and `sw.js`
- Assets: Zlicc logo files under `assets/logos/`
- Migrations: `migrations/001_schema.sql`
- Seed runner: `server/seed.js`

The front end still includes bundled seed data as an offline fallback, but when the Node API and PostgreSQL database are running, it loads from `/api/bootstrap` and persists changes to `/api/snapshot`.

## Folder Structure

```text
.
├── app.js
├── index.html
├── styles.css
├── manifest.webmanifest
├── sw.js
├── package.json
├── .env.example
├── DATABASE_SCHEMA.md
├── README_DEPLOYMENT.md
├── migrations/
│   └── 001_schema.sql
├── server/
│   ├── db.js
│   ├── index.js
│   ├── migrate.js
│   └── seed.js
└── assets/
    └── logos/
```

## Local Setup

1. Install dependencies:

```bash
npm install
```

2. Create `.env` from `.env.example`:

```bash
cp .env.example .env
```

3. Set `DATABASE_URL`:

```text
DATABASE_URL=postgres://user:password@localhost:5432/zlicc_events_crm
```

4. Run database migration:

```bash
npm run db:migrate
```

5. Seed the database from the current CRM data in `app.js`:

```bash
npm run db:seed
```

6. Start the application:

```bash
npm start
```

The application will run at:

```text
http://localhost:8080
```

## AWS Deployment

Recommended AWS setup:

- App server: ECS Fargate, Elastic Beanstalk, or EC2
- Database: RDS PostgreSQL or Aurora PostgreSQL
- Static/media storage: S3
- CDN/SSL: CloudFront + ACM
- Secrets: AWS Secrets Manager or SSM Parameter Store

### Minimum Production Path

1. Create an RDS PostgreSQL database.
2. Set `DATABASE_URL` on the app server.
3. Install Node dependencies.
4. Run `npm run db:migrate`.
5. Run `npm run db:seed` once.
6. Start with `npm start`.
7. Put Nginx or an ALB/CloudFront in front of the Node service.

## Production Database Design

The full schema is documented in:

```text
DATABASE_SCHEMA.md
```

The executable SQL migration is:

```text
migrations/001_schema.sql
```

The migration includes normalized tables for:

- tenants
- users
- tenant_modules
- companies
- contacts
- leads
- lead_contacts
- lead_activities
- meetings
- pitches
- projects
- project_line_items
- project_tasks
- sop_templates
- sop_template_items
- project_sops
- project_sop_items
- feedback_templates
- feedback_template_fields
- feedback_template_checkboxes
- project_feedback_forms
- feedback_responses
- attachments
- import_jobs
- audit_logs

It also includes `app_snapshots`, which allows the current UI to persist its full working CRM state while the app is being moved module-by-module to normalized API endpoints.

## Important Implementation Note

This build now uses PostgreSQL for persistence through the Node API. The immediate persistence bridge is the `app_snapshots` table, which stores the current UI state as JSONB. The normalized database tables are already created and ready for production-grade module APIs.

Recommended next backend hardening steps:

- Add login/authentication with Cognito/Auth0/custom JWT.
- Replace snapshot persistence with module-level CRUD APIs.
- Enforce tenant-level authorization in every endpoint.
- Move file uploads to S3.
- Add SendGrid and Zlicc WhatsApp workers.
- Add audit logs for every create/update/delete action.

## PWA Notes

This build includes:

- installable manifest
- service worker cache
- theme color/icons
- offline app shell

The app can be installed from supported browsers once served over HTTPS or `localhost`.
