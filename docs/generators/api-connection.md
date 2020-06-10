# Sub-generator: api-connection

Adds an [Api Connection](https://docs.microsoft.com/en-us/azure/connectors/apis-list) to to your solution.

```pwsh
yo armed:api-connection
```

This will prompt you to select which existing [deployment](./deployments.md) in your solution you want to add the api connection to. 

**Note**: an error will be generated if your solution does not contain any deployments.

<!-- TODO: replace with image -->
```pwsh
? Select a deployment (Use arrow keys)
❯ my-deployment
  my-other-deployment
  ──────────────
  Get me out of here!
```

You will then be prompted for a name for your api connection:

<!-- TODO: replace with image -->
```text
? Your api connection name my-api-connection
```

The generator creates a file for the api-connection in the `api-connections` folder of the the solution.  The `api-connections` folder will be created if it does not already exist.

```text
deployments
└── my-deployment
    └── api-connections
        └── my-api-connection.json
```

This is confirmed by the generator with output similar to:

```text
    create deployments\core\api-connections\my-api-connection.json
```

## Files

Each of the files created by the generator are explained below:

### {{api-connection-name}}.json

This file contains the definition of the api connection.

```json
{
  "name": "my-api-connection",
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
