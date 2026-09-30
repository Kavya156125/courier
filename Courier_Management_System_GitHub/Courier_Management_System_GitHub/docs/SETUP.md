# Salesforce Setup and Deployment

## 1. Prerequisites

- Salesforce Developer Org
- Salesforce CLI (`sf`)
- Git
- VS Code with Salesforce Extension Pack (recommended)

## 2. Authenticate

```bash
sf org login web --alias cms-dev
```

## 3. Validate

```bash
sf project deploy start --source-dir force-app --target-org cms-dev --dry-run
```

## 4. Deploy

```bash
sf project deploy start --source-dir force-app --target-org cms-dev
```

## 5. Open Org

```bash
sf org open --target-org cms-dev
```

## 6. Post-deployment

Check the manual setup document for profiles, role hierarchy, Lightning App navigation, report folders, dashboard sharing, and any metadata not supported by the selected API/version.
