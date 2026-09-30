# MASTER PROMPT — COMPLETE THE COURIER MANAGEMENT SYSTEM (SALESFORCE)

You are a senior Salesforce developer and project-completion engineer.

Complete the attached/linked project specification named "Courier Management System (CMS) NM.pdf" as a production-style Salesforce DX project that can be version-controlled and uploaded to GitHub.

SOURCE OF TRUTH
Use the supplied Courier Management System PDF as the primary specification. Preserve its terminology, object names, fields, relationships, validation rules, automation, profiles/roles, reports, dashboard, and project flow. Do not silently replace Salesforce with another technology.

PROJECT GOAL
Build a complete Salesforce Courier Management System that centralizes:
- Customer management
- Shipment booking and tracking
- Delivery-agent assignment
- Branch management
- Delivery status updates
- Invoice/billing records
- Validation and automation
- Role/profile-based access
- Reports and dashboards

REQUIRED CUSTOM OBJECTS
1. Customer__c
2. Shipment__c
3. Delivery_Agent__c
4. Branch__c
5. Delivery_Update__c
6. Invoice__c

REQUIRED RELATIONSHIPS
- Shipment__c.Customer__c -> Customer__c (Lookup)
- Shipment__c.Assigned_Agent__c -> Delivery_Agent__c (Lookup)
- Delivery_Agent__c.Branch__c -> Branch__c (Lookup)
- Delivery_Update__c.Shipment__c -> Shipment__c (Master-Detail)
- Invoice__c.Shipment__c -> Shipment__c (Lookup)

REQUIRED FIELDS
Customer:
- Name: Text, required
- Email__c: Email, required
- Phone__c: Phone, required
- Address__c: Text Area, required
- Customer_Type__c: Picklist: Regular, Business; required
- City__c: Text
- State__c: Text
- Pincode__c: Text
- Is_Active__c: Checkbox

Shipment:
- Name: Auto Number SHP-{00000}
- Customer__c: Lookup(Customer), required
- Source_Address__c: Text Area, required
- Destination_Address__c: Text Area, required
- Weight__c: Number, required
- Price__c: Currency, required
- Status__c: Picklist: Booked, In Transit, Out for Delivery, Delivered, Cancelled; required
- Expected_Date__c: Date, required
- Assigned_Agent__c: Lookup(Delivery_Agent)
- Shipment_Type__c: Picklist: Domestic, International; required

Delivery Agent:
- Name: Text, required
- Email__c: Email, required
- Phone__c: Phone, required
- Branch__c: Lookup(Branch), required
- Status__c: Picklist: Active, Inactive, On Leave; required
- Joining_Date__c: Date

Branch:
- Name: Text, required
- Branch_Code__c: Text, required
- City__c: Text, required
- State__c: Text, required
- Manager_Name__c: Text

Delivery Update:
- Name: Auto Number UPD-{0000}
- Shipment__c: Master-Detail(Shipment), required
- Status__c: Picklist: In Transit, Out for Delivery, Delivered, Delayed; required
- Update_Date__c: DateTime, required
- Remarks__c: Text

Invoice:
- Name: Auto Number INV-{0000}
- Shipment__c: Lookup(Shipment), required
- Amount__c: Currency, required
- Invoice_Date__c: Date, required
- Payment_Status__c: Picklist: Paid, Unpaid, Pending; required

VALIDATION RULES
Implement the rules from the specification:
Customer:
- Email_Required: ISBLANK(Email__c)
- Validate_Phone_Number: LEN(Phone__c) <> 10
- Validate_Pincode: LEN(Pincode__c) <> 6
Shipment:
- Validate_Weight: Weight__c <= 0
- Validate_Price: Price__c <= 0
- Validate_Expected_Date: Expected_Date__c < TODAY()
Delivery Agent:
- Validate_Agent_Email: NOT(CONTAINS(Email__c, "@"))
Branch:
- Branch_Code_Required: ISBLANK(Branch_Code__c)
Delivery Update:
- Remarks_Required_For_Delay:
  AND(
    ISPICKVAL(Status__c, "Delayed"),
    ISBLANK(Remarks__c)
  )

AUTOMATION
Implement the documented record-triggered flow:
- Object: Delivery_Update__c
- Trigger: when a record is created
- Find related Shipment__c using Delivery_Update__c.Shipment__c
- Set Shipment__c.Status__c = Delivery_Update__c.Status__c
- Flow label/API name: Auto_Update_Shipment_Status
- Activate it when deployment is complete

APP
Create a Lightning App named:
Courier Management System

Include tabs/navigation for:
- Customers
- Shipments
- Delivery Agents
- Branches
- Delivery Updates
- Invoices
- Reports
- Dashboards

PAGE LAYOUTS
Create clear sections matching the specification:
Customer:
- Customer Information
- Address Details
Shipment:
- Shipment Details
- Address Information
- Delivery Information
Delivery Agent:
- Agent Details
- Additional Information
Branch:
- Branch Information
Delivery Update:
- Update Information
Invoice:
- Invoice Details

SECURITY
Document and, where metadata support is practical, configure:
- Courier Admin
- Branch Manager
- Delivery Agent
- Customer Support

Use least-privilege permissions consistent with the PDF:
Branch Manager: create/read/edit customers and shipments; read/edit agents and branches; create/read/edit delivery updates; read invoices.
Delivery Agent: read/edit shipments; create/read/edit delivery updates; read customers and invoices; no branch editing; no delete permissions.
Customer Support: read/edit customers and shipments; read delivery updates and invoices.

If Salesforce metadata/API limitations prevent exact profile deployment, provide deployable permission sets plus a clearly documented manual setup checklist. Do not fake unsupported metadata.

REPORTS AND DASHBOARD
Implement/document:
- Shipment Status Summary
- Agent Performance Report
- Revenue by Branch Report
- Courier Management Dashboard

Dashboard components:
- Shipment Status Overview — Donut Chart
- Agent Performance — Bar Chart
- Revenue by Branch — Column Chart

TESTING
Create meaningful Apex tests only where Apex is used. For declarative functionality, create a detailed manual test matrix covering:
1. Customer creation
2. Invalid email/phone/pincode
3. Shipment creation
4. Invalid weight/price/date
5. Delivery-agent assignment
6. Delayed update without remarks
7. Delivery update automatically changing shipment status
8. Invoice creation
9. Role/profile access
10. Reports/dashboard visibility

GITHUB REQUIREMENTS
Create a clean Salesforce DX repository:
- sfdx-project.json
- force-app/main/default/...
- README.md
- .gitignore
- docs/SETUP.md
- docs/TESTING.md
- docs/SALESFORCE_MANUAL_SETUP.md
- docs/PROJECT_SPECIFICATION.md

Do NOT include:
- Salesforce passwords
- security tokens
- OAuth secrets
- session IDs
- real customer information
- real employee information
- private emails
- generated credentials

README MUST INCLUDE
- Project title
- Overview
- Problem statement
- Features
- Architecture
- Object model
- Relationships
- Automation
- Security
- Reports/dashboard
- Installation/deployment
- Testing
- GitHub upload commands
- Known Salesforce manual setup limitations
- Future scope

DEPLOYMENT QUALITY
Before declaring completion:
1. Check metadata naming/API names.
2. Check object relationships.
3. Check picklist values.
4. Check validation formulas.
5. Check flow references.
6. Ensure no secret/credential is committed.
7. Ensure README matches actual repository contents.
8. Provide deployment commands.
9. Provide a final checklist of anything that still must be configured manually in a Salesforce Developer Org.

IMPORTANT
Do not claim that a Salesforce feature was implemented if it is only documented.
Do not invent screenshots, Salesforce IDs, deployment results, test results, or credentials.
If something cannot be represented safely in source metadata, explicitly mark it as MANUAL SETUP and explain the exact steps.

FINAL OUTPUT
Return:
A. Completed Salesforce DX source
B. README
C. Deployment/setup documentation
D. Testing checklist
E. GitHub-ready ZIP
F. A concise list of remaining manual Salesforce steps, if any
