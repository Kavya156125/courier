# Courier Management System (CMS)

Salesforce-based Courier Management System derived from the supplied project specification.

## Purpose

The system centralizes customer management, shipment booking/tracking, delivery-agent assignment, branch operations, delivery updates, invoices, automation, security, reports, and dashboards.

## Technology

- Salesforce Lightning
- Salesforce Custom Objects
- Salesforce Flows
- Validation Rules
- Profiles / Permission Sets
- Reports & Dashboards
- Salesforce DX source format

## Custom Objects

| Object | API Name |
|---|---|
| Customer | `Customer__c` |
| Shipment | `Shipment__c` |
| Delivery Agent | `Delivery_Agent__c` |
| Branch | `Branch__c` |
| Delivery Update | `Delivery_Update__c` |
| Invoice | `Invoice__c` |

## Main Automation

`Auto_Update_Shipment_Status` updates the related Shipment status whenever a Delivery Update is created.

## Repository Contents

- `PROJECT_COMPLETION_PROMPT.md` — master prompt for completing/validating the project with an AI coding agent
- `force-app/main/default/` — Salesforce metadata source
- `docs/SETUP.md` — setup/deployment guide
- `docs/TESTING.md` — test checklist
- `docs/SALESFORCE_MANUAL_SETUP.md` — items that may require configuration in a Salesforce Developer Org
- `docs/PROJECT_SPECIFICATION.md` — concise specification extracted from the project document

## Deployment

Authenticate to a Salesforce org with Salesforce CLI, then deploy:

```bash
sf org login web --alias cms-dev
sf project deploy start --source-dir force-app --target-org cms-dev
```

Validate first:

```bash
sf project deploy start --source-dir force-app --target-org cms-dev --dry-run
```

## Important

Never commit Salesforce credentials, access tokens, security tokens, session IDs, or real customer data.

## Future Scope

- Mobile tracking
- GPS integration
- SMS notifications
- AI-based delivery optimization
