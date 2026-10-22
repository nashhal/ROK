# ROCK — Commerce Operations Demo

A standalone, Arabic-first operations dashboard for exploring the ROCK workflow. This repository is separate from the existing storefront repository at `nashhal/ROCK`.

## What's in this commit

- `index.html`: responsive RTL/LTR dashboard with Arabic/English toggle.
- Overview, catalog, orders, inventory, purchasing, couriers, customers, payments, reports, invoices, promotions, support, audit-log, and settings screens.
- Demo product and order records to make the interface explorable.
- Local-only product/order editing, stock adjustments, status updates, CSV export, JSON export/import, and print-to-PDF demo receipts.

## Try it

Open `index.html` in a current browser, or serve this directory:

```bash
python -m http.server 8000
```

Then visit `http://localhost:8000/`.

## Important limitations

This is a **front-end prototype**, not a deployable production commerce system. All state is saved in the current browser's `localStorage`; employees do not share data between devices. Authentication, server-side roles, MySQL, OTP, actual messages, payment capture, courier integrations, tax-compliant invoices, and remote backups are not implemented. Seeded records are examples; listed amounts are not actual revenue or money collected.

Do not enter real customer, payment, or business-sensitive data. Do not use this demo as the live order-management system.

## Before production

Build the server-side API and database, enforce authentication and role permissions on the server, set up real integrations and secrets management, implement verified backup/restore and monitoring, and run security, accessibility, integration, and acceptance tests. Static hosting alone does not provide these features.

## Current catalogue note

This dashboard uses a small sample catalogue for interface testing. It does **not** replace the 41-product store catalogue or include the product-image library from the local review package. Those assets must be integrated in the production implementation after the backend and deployment target are finalized.
