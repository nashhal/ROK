# Security policy

## Scope

This repository currently contains a browser-only demonstration dashboard. It is not an authenticated application and must not be used for production business operations.

## Do not submit

Do not create issues or commits containing passwords, API keys, access tokens, customer names or telephone numbers, payment details, private supplier quotes, or confidential business records.

## Reporting

For a suspected security issue, contact the repository owner privately through GitHub's supported private reporting/contact route. Do not publish exploit details or real customer data in a public issue.

## Current limitations

- No server-side authentication or authorization.
- No shared database or server-side audit log.
- No live payment, SMS, WhatsApp, email, or shipping integration.
- Browser localStorage data is not encrypted or centrally backed up.
- Demo receipts are not tax invoices and demo payment flags are not proof of collection.

These limitations must be addressed and independently tested before production use.
