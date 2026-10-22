# ROCK platform production-readiness plan

This document defines the work required to turn the current interface demo into a production commerce-operations platform. The checklist is intentionally explicit: UI interactions in the demo are local simulations, not proof that a real workflow is implemented.

## Target architecture

- **Web client:** responsive Arabic/English RTL/LTR UI, accessibility, validated forms, and clearly separated demo/production environments.
- **Application API:** server-side business logic, schema validation, rate limiting, idempotent order/payment operations, and authorization on every protected route.
- **Database:** relational schema and migration history for products, variants, warehouses, inventory movements, purchase orders, customers, orders, order items, payment attempts, shipments, invoices, returns, promotions, support tickets, users, roles, and audit events.
- **Background jobs:** retryable notification and fulfillment jobs with a dead-letter strategy and observable status.
- **Integrations:** payment provider, shipping/courier provider, SMS/OTP, email, and WhatsApp Business only after credentials, sandbox tests, and delivery/consent rules have been approved.
- **Operations:** managed secrets, structured logs, metrics, alerts, backup/restore tests, staging environment, and a rollback plan.

## Roles and permissions

Define a least-privilege matrix before coding the production API. Example roles: owner, administrator, catalog manager, warehouse operator, purchasing, customer service, finance, and courier. Permission checks must run on the server; hiding a button in the browser is not authorization.

## Data integrity requirements

- Store money as fixed-precision decimal values or integer minor units; do not use floating-point arithmetic as the source of truth.
- Record inventory changes as auditable movements. Prevent negative stock and prevent duplicate order fulfillment.
- Use explicit order and payment state machines. A client-side flag must never mark real money as collected.
- Keep invoice numbering and tax fields server-generated under the applicable jurisdiction's requirements.
- Validate and normalize inputs on the server; parameterize database queries.
- Record who changed a critical value, the time, and an appropriate before/after snapshot without logging secrets.

## Security and privacy baseline

- Secure authentication, session rotation/expiry, multi-factor or OTP policies, brute-force controls, and account recovery.
- Server-enforced authorization and separation of duties for payment, refunds, stock adjustments, and user administration.
- TLS in transit, encrypted provider secrets, restricted database access, and no production credentials in Git.
- CSRF protection where cookie sessions are used, secure cookies, output encoding, request-size limits, and rate limits.
- Data-retention and deletion policies, consent for marketing messages, and controlled access to customer contact details.
- Tested point-in-time or scheduled database backups with documented restoration objectives and periodic restore drills.

## Suggested implementation order

1. Confirm the hosting target and supported runtime; the current demo alone does not specify whether to use PHP/MySQL, Node.js, or another stack.
2. Approve the entities, order/payment state machines, user roles, and ownership of each operational workflow.
3. Implement database migrations and authenticated server API, then integration and authorization tests.
4. Connect catalog, stock, purchase orders, order management, and delivery workflows to the API.
5. Add payments, receipts/invoices, customer notifications, returns, promotions, and support with sandbox providers first.
6. Add monitoring, audit review, backups, restore tests, rate limiting, and incident response.
7. Complete mobile/accessibility, cross-browser, load, security, data migration, and end-to-end acceptance tests in staging.
8. Migrate verified catalogue/media, take a restorable backup, and deploy through a rehearsed release/rollback plan.

## Release gate

Do not enable live orders until all of the following are true: production auth and roles pass tests; the database and migrations are deployed; payment/shipping/notification test transactions succeed; duplicate requests are safely handled; backups have been restored in a rehearsal; privacy and invoice requirements have been reviewed; and the business owner has signed off on end-to-end testing.
