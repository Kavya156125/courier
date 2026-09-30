# Testing Checklist

| ID | Test | Expected Result |
|---|---|---|
| T01 | Create valid Customer | Record saves |
| T02 | Blank customer email | Validation error |
| T03 | Invalid phone length | Validation error |
| T04 | Invalid pincode length | Validation error |
| T05 | Create valid Shipment | Record saves |
| T06 | Weight <= 0 | Validation error |
| T07 | Price <= 0 | Validation error |
| T08 | Expected date in past | Validation error |
| T09 | Create Delivery Update | Record saves |
| T10 | Delayed update without remarks | Validation error |
| T11 | Delivery Update with status | Related Shipment status changes automatically |
| T12 | Create Invoice | Record saves |
| T13 | Delivery Agent access | Restricted from branch editing/deleting |
| T14 | Customer Support access | Limited to documented objects |
| T15 | Dashboard | Charts display report data |

Record evidence/screenshots in the project report only after the tests are actually executed in Salesforce.
