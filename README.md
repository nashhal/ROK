# ROCK — Commerce Operations Demo

A standalone, Arabic-first operations dashboard for exploring ROCK commerce workflows. This repository is separate from the existing storefront repository at `nashhal/ROCK`.

## Project layout

- `index.html`: semantic page shell and interface landmarks.
- `assets/app.css`: responsive styling, RTL/LTR layouts, tables, cards, forms, and mobile navigation.
- `assets/app.js`: browser-only demo workflows, sample records, local persistence, CSV and JSON export/import, and demo receipt printing.
- `.github/workflows/validate.yml`: JavaScript syntax and basic interface structure check.
- `SECURITY.md`: scope, reporting, and limitations.
- `docs/PRODUCTION-READINESS.md`: target architecture, security baseline, and staged launch plan.

## Included screens

Overview, products/catalog, orders, inventory, purchasing/suppliers, couriers/delivery, customers, payments, reports, invoices, promotions, customer support, audit log, and settings. The interface supports Arabic and English and adapts between right-to-left and left-to-right layouts.

## Try it

Open `index.html` in a modern browser, or serve the directory:

```bash
python -m http.server 8000
```

Then visit `http://localhost:8000/`.

## Important limitations

This is a **front-end prototype**, not a production commerce system. All state is saved in the current browser's `localStorage`; employees do not share data between devices. Authentication, server-side roles, MySQL, OTP, actual messages, payment capture, courier integrations, tax-compliant invoices, and remote backups are not implemented. Seeded records are examples; listed amounts are not actual revenue or money collected.

Do not enter real customer, payment, or confidential business data. Do not use this demo for live order processing.

## Catalogue scope

This interface currently uses eight sample products to make the UI explorable. It does **not** replace the existing 41-product store catalogue or include the product-photo library from the review package.

## Before production

Implement the server-side API and database, enforce authentication and roles on the server, add verified integrations and secrets management, establish tested backup/restore and monitoring, and run security, accessibility, integration, and acceptance tests. Static hosting alone does not provide these features.
