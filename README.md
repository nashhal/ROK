# ROCK | Commerce & Operations Platform

This repository contains the ROCK standalone operations-platform demo. It is kept separate from the existing production storefront repository `nashhal/ROCK`.

## Current package scope

- Arabic-first RTL interface with an English toggle
- Store, administrator, and courier workspaces
- Demo workflows for catalog, orders, stock, purchasing, barcodes, customers, payments, shipping, returns, promotions, reports, invoices, notifications, audit, security, and settings
- Local browser persistence for demonstration only

## Important: not production-ready

The current prototype uses browser `localStorage` and seeded example records. It does **not** include a production backend, shared employee accounts, server-side permission enforcement, MySQL migrations, OTP delivery, real SMS/WhatsApp/email, payment verification, courier integrations, or verified remote backups. Do not enter real customer, payment, or confidential business data.

A static GitHub Pages deployment is not a substitute for a secure server-side application. Before real operations, implement and test the API, database, authentication, role-based access control, audit trail, secrets management, integrations, backup/restore, privacy controls, and end-to-end security.

## Project layout

- `prototype/`: isolated browser-only operations demo.
- `products.js`: storefront product catalogue snapshot when included in the package.
- `assets/`: brand and product media when included in the package.

## Running locally

Serve the repository root using a local static server, then open `/prototype/`. For example:

```bash
python -m http.server 8000
```

Open `http://localhost:8000/prototype/`.

## Production checklist

- [ ] Build the server-side API and database migrations
- [ ] Enforce authentication and role permissions on the server
- [ ] Integrate real payment, notification, and shipping providers
- [ ] Add validated backup and restore, monitoring, and audit controls
- [ ] Run accessibility, browser, integration, and security tests
- [ ] Replace demo data and complete acceptance testing before launch
