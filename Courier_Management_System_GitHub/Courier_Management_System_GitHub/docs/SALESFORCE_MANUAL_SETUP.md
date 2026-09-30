# Salesforce Manual Setup Checklist

These items should be verified in the target Salesforce Developer Org because some org-specific configuration is not reliably represented as portable source metadata.

- Create/verify Lightning App: Courier Management System
- Add Customer, Shipment, Delivery Agent, Branch, Delivery Update, Invoice, Reports, Dashboards tabs
- Configure role hierarchy:
  - Courier Admin
  - Branch Manager
  - Delivery Agent
  - Customer Support
- Configure user profiles/permission sets according to the project specification
- Create report folder: CMS Reports
- Create and verify:
  - Shipment Status Summary
  - Agent Performance Report
  - Revenue by Branch Report
- Create and verify Courier Management Dashboard
- Share dashboard with the intended roles
- Activate the Auto_Update_Shipment_Status flow
- Create test records and execute the testing checklist
