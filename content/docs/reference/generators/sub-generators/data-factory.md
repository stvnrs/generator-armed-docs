---
title: "data-factory sub-generator"
linkTitle: "data-factory"
---

Adds an [data factory](https://azure.microsoft.com/en-us/services/data-factory/) to to your solution.

```pwsh
yo armed:data-factory
```

This will prompt you to select which existing [deployment](./deployments.md) in your solution you want to add the data factory to.

**Note**: an error will be generated if your solution does not contain any deployments.

<!-- TODO: replace with image -->
```pwsh
? Select a deployment (Use arrow keys)
❯ my-deployment
  my-other-deployment
  ──────────────
  Get me out of here!
```

You will then be prompted for a name for your data-factory:

<!-- TODO: replace with image -->
```text
? Your data-factory name my-data-factory
```

The generator creates a folder for the data-factory in the `data-factories` folder of the the solution.  The `data-factories` folder will be created if it does not already exist.

```text
deployments
└── my-deployment
    └── data-factories
        └── my-data-factory
            └── _data-factory.json
```

This is confirmed with output similar to:

```text
    create deployments\my-deployment\data-factories\my-data-factory\_data-factory.json
```

## Files

Each of the files create by the generator are explained below:

### _data-factory.json

This file contains the declaration of the data factory.

```json
{
  "name": "my-data-factory",
  "type": "Microsoft.Web/connections",
  "apiVersion": "2016-06-01",
  "location": "[resourceGroup().location]",
  "properties": {
    "displayName": "",
    "customParameterValues": {},
    "api": {
      "id": ""
    },
    "parameterValues": {

    }
  }
}
```
