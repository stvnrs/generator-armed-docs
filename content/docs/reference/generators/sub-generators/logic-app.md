---
title: "logic-app sub-generator"
linkTitle: "logic-app"
---

Adds a [Logic App](https://azure.microsoft.com/en-us/services/logic-apps/) to to your solution.

```pwsh
yo armed:logic-app
```

This will prompt you to select which existing [deployment](./deployments) in your solution you want to add the logic app to. 

**Note**: an error will be generated if your solution does not contain any deployments.

<!-- TODO: replace with image -->
```pwsh
? Select a deployment (Use arrow keys)
❯ my-deployment
  my-other-deployment
  ──────────────
  Get me out of here!
```

You will then be prompted for a name for your logic app:

<!-- TODO: replace with image -->
```text
? Your logic app name my-logic-app
```

and it will create the following:

```text
deployments
└── my-deployment
    └── logic-apps
        └── my-logic-app
            ├── _logic-app.json
            ├── parameters.json
            └── definition.json
```

This is confirmed with output similar to:

```text
    create deployments\core\logic-apps\my-logic-app\_logic-app.json
    create deployments\core\logic-apps\my-logic-app\parameters.json
    create deployments\core\logic-apps\my-logic-app\definition.json
```

## Files

### _logic-app.json

This file contains the declaration of the logic app.

```json
{
  "name": "{{logic-app-name}}",
  "type": "Microsoft.Logic/workflows",
  "location": "[resourceGroup().location)]",
  "apiVersion": "2016-06-01",
  "dependsOn": [
  ]
}
```

### parameters.json

This file contains the parameters e.g. connections for the the logic app.

```json
{
  "properties": {
    "parameters": {
      "$connections": {
        "value": {}
      }
    }
  }
}
```

### definition.json

This file contains the steps for the logic app.

```json
{
  "properties": {
    "definition": {
      "$schema": "https://schema.management.azure.com/providers/Microsoft.Logic/schemas/2016-06-01/workflowdefinition.json#",
      "actions": {}
    }
  }
}
```
