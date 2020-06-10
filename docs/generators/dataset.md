# dataset sub-generator

Adds a [dataset](https://docs.microsoft.com/en-us/azure/data-factory/concepts-datasets) to a [data factory](https://azure.microsoft.com/en-us/services/data-factory/) in your solution.

```pwsh
yo armed:dataset
```

This will prompt you to select which existing [deployment](./deployments.md) in your solution contains the [data factory](https://azure.microsoft.com/en-us/services/data-factory/) you wish to add the [dataset](https://docs.microsoft.com/en-us/azure/data-factory/concepts-datasets) to.

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

You will then be prompted for a name for your [dataset](https://docs.microsoft.com/en-us/azure/data-factory/concepts-datasets):

<!-- TODO: replace with image -->
```text
? Your dataset name my-dataset
```
The generator will create a folder for the [dataset](https://docs.microsoft.com/en-us/azure/data-factory/concepts-datasets) in the `data-factories\{{data-factory}}\datasets` folder of the the solution.  The `datasets` folder will be created if it does not already exist.

```text
deployments
└── my-deployment
    └── data-factories
        └── my-data-factory
            └── datasets
                └── my-dataset
                    └──_dataset.json
```

This is confirmed with output similar to:

```text
    create deployments\my-deployment\data-factories\my-data-factory\datasets\my-data-set\_data-factory.json
```

## Files

Each of the files create by the generator are explained below:

### _dataset.json

This file contains the main declaration of the dataset.

```json
{
  "name": "my-data-set",
  "type": "Microsoft.DataFactory/factories/datasets",
  "apiVersion": "2018-06-01",
  "dependsOn": []
}
```

### properties.json

This file contains all of the dataset's properties apart from the schema.

```json
{
  "properties": {
    "linkedServiceName": {},
    "parameters": {},
    "folder": {},
    "annotations": [],
    "type": "",
    "typeProperties": {}
  },
}
 ``` 
### schema.json

This file contains the [schema](https://docs.microsoft.com/en-us/azure/data-factory/concepts-datasets-linked-services#dataset-structure-or-schema) for the data set. **Note** this is optional.

```json
{
    "schema": {

    }
}
```
