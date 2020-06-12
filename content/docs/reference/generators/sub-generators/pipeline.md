---
title: "pipeline sub-generator"
linkTitle: "pipeline"
---

Adds a [pipeline](https://docs.microsoft.com/en-us/azure/data-factory/concepts-pipelines-activities) to a [data factory](https://azure.microsoft.com/en-us/services/data-factory/) in your solution

```pwsh
yo armed:pipeline
```

This will prompt you to select which existing [deployment](./deployments.md) in your solution contains the [data factory](https://azure.microsoft.com/en-us/services/data-factory/) you wish to add the [pipeline](https://docs.microsoft.com/en-us/azure/data-factory/concepts-pipelines-activities) to.

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

You will then be prompted for a name for your [pipeline](https://docs.microsoft.com/en-us/azure/data-factory/concepts-pipelines-activities):

<!-- TODO: replace with image -->
```text
? Your pipeline name my-pipeline
```

The generator will create a folder for the [pipeline](https://docs.microsoft.com/en-us/azure/data-factory/concepts-pipelines-activities) in the `data-factories\{{data-factory}}\pipelines` folder of the the solution.  The `pipelines` folder will be created if it does not already exist.

```text
deployments
└── my-deployment
    └── data-factories
        └── my-data-factory
            └── pipelines
                └── my-pipeline
                    └──_pipeline.json
```

This is confirmed with output similar to:

```text
    create deployments\my-deployment\data-factories\my-data-factory\pipelines\my-pipeline\_pipeline.json
```

## Files

Each of the files create by the generator are explained below:

### _pipeline.json

The main definition of the [pipeline](https://docs.microsoft.com/en-us/azure/data-factory/concepts-pipelines-activities) excluding [parameters](https://docs.microsoft.com/en-us/azure/data-factory/concepts-pipelines-activities#pipeline-json) and [activities](https://docs.microsoft.com/en-us/azure/data-factory/concepts-pipelines-activities#activity-json).

```json
{
      "name": "my-pipeline",
      "type": "Microsoft.DataFactory/factories/pipelines",
      "apiVersion": "2018-06-01",
      "properties": {
        "folder": {
          "name": ""
        },
        "annotations": []
      },
      "dependsOn": []
    }
```

### parameters.json

The file contains the [parameters](https://docs.microsoft.com/en-us/azure/data-factory/concepts-pipelines-activities#pipeline-json) for the [pipeline](https://docs.microsoft.com/en-us/azure/data-factory/concepts-pipelines-activities).

```json
 {
  "parameters": {
   }
 }
```

### activities

The file defines the [activities](https://docs.microsoft.com/en-us/azure/data-factory/concepts-pipelines-activities#activity-json) for the [pipeline](https://docs.microsoft.com/en-us/azure/data-factory/concepts-pipelines-activities).

```json
{
  "activities": {
   }
 }
```
