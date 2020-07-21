---
title: "data-flow sub-generator"
linkTitle: "data-flow"
---

Adds a [data-flow](https://docs.microsoft.com/en-us/azure/data-factory/concepts-data-flows) to a [data factory](https://azure.microsoft.com/en-us/services/data-factory/) in your solution.

```pwsh
yo armed:data-flow
```

This will prompt you to select which existing [deployment](./deployments) in your solution contains the [data factory](https://azure.microsoft.com/en-us/services/data-factory/) you wish to add the [data-flow](https://docs.microsoft.com/en-us/azure/data-factory/concepts-data-flow-overview) to.

**Note**: an error will be generated if your solution does not contain any deployments.

<!-- TODO: replace with image -->
```pwsh
? Select a deployment (Use arrow keys)
❯ my-deployment
  my-other-deployment
  ──────────────
  Get me out of here!
```

After selecting a deployment you will be prompted to select a data factory from that deployment.

**Note**: an error will be generated if your deployment does not contain any data factories.

<!-- TODO: replace with image -->
```pwsh
? Select a deployment (Use arrow keys)
❯ my-data-factory
  my-other-data-factory
  ──────────────
  Get me out of here!
```

You will then be prompted for a name for your [data-flow](https://docs.microsoft.com/en-us/azure/data-factory/concepts-data-flows):

<!-- TODO: replace with image -->
```text
? Your data-flow name my-data-flow
```
The generator will create a folder for the [data-flow](https://docs.microsoft.com/en-us/azure/data-factory/concepts-data-flows) in the `data-factories\{{data-factory}}\data-flows` folder of the the solution.  The `data-flows` folder will be created if it does not already exist.

```text
deployments
└── my-deployment
    └── data-factories
        └── my-data-factory
            └── data-flows
                └── my-data-flow
                    └──_data-flow.json
```

This is confirmed with output similar to:

```text
    create deployments\my-deployment\data-factories\my-data-factory\data-flows\my-data-set\_data-factory.json
```

## Files

Each of the files create by the generator are explained below:
